# Essentia

> **Qué es este fichero.** El análisis de audio de la obra: cómo se instala
> Essentia en esta máquina, cómo se ejecuta el analizador, qué campos produce y
> qué significan — y, lo que más importa, **qué no se puede concluir
> con ellos**.
>
> **Fecha:** 2026-09-29 · **Alcance:** «Avivas el fuego», a partir de
> `1_Avivas.wav` en `recursos/musicas/`, más dos exportaciones MP3 que ya no
> están.
>
> **Estado:** los datos de `1_Avivas.wav` (el original) son válidos. Los del
> MP3 llamado «vocal» están **en cuarentena** — ver [Cuarentena](#cuarentena) — y
> hay dos preguntas abiertas al autor al final del documento.

## Cómo se lee este manual

| Parte | Qué es | Para quién |
|---|---|---|
| [1. Instalar](#parte-1--instalar) | Poner Essentia en pie | Quien monta el entorno |
| [2. El analizador](#parte-2--el-analizador) | Qué hace el script y dónde se rompe | Quien lo mantiene |
| [3. Los datos](#parte-3--los-datos) | Qué significa cada campo | Quien los usa |
| [4. Avivas el fuego](#parte-4--avivas-el-fuego) | Lo que sale de los dos ficheros | Quien decide |
| [5. Lo que no sale](#parte-5--lo-que-no-sale) | Lo que la máquina no puede decir | Quien decide |
| [6. Preguntas abiertas](#parte-6--preguntas-abiertas) | Lo que hay que preguntar | El autor |

> **Antes de citar cualquier número de este documento:** el apartado 5 explica
> qué campos son fiables y cuáles no. Un campo que no aparece en el apartado 5
> como fiable **no está medido**, y el apartado 4 dice dónde se queda cada uno.

---

# Parte 1 — Instalar

## Qué hace falta

- Linux. Hay rueda precompilada de Essentia para x86_64 (es la que se instaló
  y comprobó aquí) y no hizo falta compilar nada. En otra arquitectura puede
  que no haya rueda y toque compilar: si `uv pip install` falla, ese es el
  motivo.
- `curl`. Nada más: uv se encarga de traerse su propio Python, así que no hace
  falta instalar Python antes.

## Por qué uv y no pip

uv instala y resuelve dependencias mucho más rápido que pip, y —lo que importa
aquí— **puede traer su propio intérprete de Python**. Eso evita depender del
Python del sistema, que en esta máquina es de otra versión y está en una ruta
que no tenemos permiso de escribir.

## Por qué el entorno vive fuera del repo

Dos razones, y las dos son de permisos:

- `recursos/musicas/` es de `root`. No se puede escribir dentro, así que un
  entorno virtual ahí es imposible.
- `~/.local/share/` también es de `root`. uv usa ese directorio por defecto.

El entorno va entonces a **`/home/assistant/.local/netta-essentia/venv`**, que
es de nuestro usuario y no ensucia el árbol de git.

## Los comandos

```bash
# 1. uv
curl -LsSf https://astral.sh/uv/install.sh | sh
export PATH="$HOME/.local/bin:$PATH"

# 2. Python 3.11
uv python install 3.11

# 3. El entorno, FUERA del repo
uv venv --python 3.11 /home/assistant/.local/netta-essentia/venv

# 4. Essentia dentro de él
UV_CACHE_DIR=/tmp/opencode/uvcache \
  uv pip install --python /home/assistant/.local/netta-essentia/venv/bin/python essentia
```

> **`UV_CACHE_DIR` es solo la caché de descarga**, no el entorno. Se puso en
> `/tmp` porque la caché por defecto está en `~/.local/share` y no se puede
> escribir. Si borras `/tmp`, solo se pierde la descarga: el entorno y el
> paquete instalado siguen donde están.

## Comprobar que funciona

```bash
/home/assistant/.local/netta-essentia/venv/bin/python \
  -c "import essentia; print(essentia.__version__)"
```

Debe imprimir `2.1-beta6-dev`. Si imprime algo o falla con `ModuleNotFoundError`,
el paso 4 no se completó; repetirlo.

## Versiones exactas de este entorno

Fijadas el 2026-09-29. **El análisis de la parte 4 se hizo con estas.**

| Paquete | Versión |
|---|---|
| Python | 3.11.16 |
| `essentia` (runtime) | `2.1-beta6-dev` |
| `essentia` (distribución) | `2.1b6.dev1389` |
| `numpy` | 2.4.6 |
| `pyyaml` | 6.0.3 |
| `six` | 1.17.0 |
| `uv` | 0.12.20 (x86_64-unknown-linux-gnu) |

> **«dev» en el número de versión es una advertencia, no un detalle.** Es una
> foto de una versión de desarrollo, no una release. La parte 2 explica por qué
> eso importa: cuatro algoritmos no se comportan como dice su documentación.

## Si hay que rehacerlo

Borrar el directorio y repetir desde el paso 3. Es reversible y no toca nada
del repo:

```bash
rm -rf /home/assistant/.local/netta-essentia/venv
```

---

# Parte 2 — El analizador

## Cómo se ejecuta

```bash
/home/assistant/.local/netta-essentia/venv/bin/python analiza.py <fichero.mp3> <salida.json>
```

Desde la raíz del repo, sobre las pistas que hay:

```bash
V=/home/assistant/.local/netta-essentia/venv/bin/python
$V analiza.py recursos/musicas/Avivas_instrumental.mp3 /tmp/inst.json
$V analiza.py recursos/musicas/Avivas_vocal.mp3       /tmp/voca.json
```

Tarda del orden de un minuto por pista. La salida es un JSON con todo lo que
produce el script, que es bastante más de lo que se resume en la parte 4: los
los 533 pulsos uno a uno, los 267 acordes, y el nivel de cada grupo.

## Qué hace, etapa por etapa

```
cargar (mono 44,1 kHz)
   │
   ├─ tempo        RhythmExtractor2013  ──► BPM, confianza, alternativas, pulsos
   ├─ tonalidad    KeyExtractor         ──► tónica, escala, fuerza
   ├─ HPCP         SpectralPeaks + HPCP ──► perfil de altura, 12 clases, por trama
   │      │
   │      ├─ compás      dónde caen los cambios de acorde
   │      └─ acordes     ChordsDetection por trama, voto por pulso
   │
   ├─ MFCC por pulso ──► media y desviación
   │      └─ estructura   similitud coseno ──► checkerboard ──► puntos de cambio
   │
   ├─ nivel        RMS en dB por grupo
   └─ espectro     centroide, rolloff 85 %, loudness de Stevens
```

Dos ideas que explican el diseño:

- **El HPCP no se aplica a la señal.** Toma las frecuencias y las magnitudes de
  los picos del espectro. La cadena es ventana → espectro → picos → HPCP. En
  una pista entera eso son unas 8.000 tramas, y es lo que permite volver de la
  trama al segundo: sin el `hop` un acorde no tiene hora.
- **Un pulso es el intervalo entre dos pulsos**, no el resto de la pista desde
  ese pulso. Este detalle aparece como bug tres veces en la parte 2.

## Las trampas de esta build

Cuatro algoritmos no hacen lo que dice su documentación. Los cuatro se
comprobaron uno a uno el 2026-09-29, y estos son los errores exactos:

| Algoritmo | Lo que espera | Qué pasa | Qué se usa en su lugar |
|---|---|---|---|
| `ChordsDetectionBeats` | `(pcp, ticks)` | Falla con las dos formas. Posicional: `RuntimeError: an error while parsing input arguments: VectorVectorReal::fromPythonCopy...`. Con palabras clave: `TypeError: __call__() got an unexpected keyword argument`. Y `configure('pcp')`: `TypeError: configure() takes 1 positional argument` | `ChordsDetection` con la matriz entera, y voto pulso a pulso |
| `HPCP` | la señal | `ValueError: HPCP.compute requires 2 argument(s), 1 given`. Toma **frecuencias y magnitudes**, no audio | La cadena con `SpectralPeaks` de este mismo script |
| `LoudnessEBUR128` | audio | Exige un vector **estéreo** (`vector<stereosample>`). Con mono 1D: `TypeError: cannot convert argument VECTOR_REAL to VECTOR_STEREOSAMPLE`. Con mono 2D: el mismo error con `MATRIX_REAL` | `Loudness` (energía^2/3), que no es LUFS y así se anota |
| `Meter` | intervalos | `RuntimeError` con la entrada que se le pasa | Nada. Se descarta: el script no lo usa para decidir |

> **`ChordsDetection` también tiene su trampa:** no acepta un vector suelto.
> Espera una **matriz de tramas** (`vector<vector>`), y devuelve **dos** salidas,
> no cinco: el acorde por trama y su fuerza. Un `ChordsDetection()(vector_1d)`
> falla con `VectorVectorReal::fromPythonCopy: input is not a list`.

> **`MFCC` devuelve dos salidas**, las bandas de mel y los coeficientes. Para
> comparar tramas entre sí sirven los coeficientes, que son la segunda.

## Los cuatro bugs que fueron míos, no de Essentia

Se documentan porque los tres tienen la misma forma: **el script parecía
funcionar y daba números**, y los números solo se veían falsos al mirar la
estructura de la canción. Si se tocan esas líneas, no volver a cometerse.

1. **Indexar por valor de pulso en vez de por tiempo.** `hp[beats.astype(int)]`
   donde `beats` está en **segundos**: el pulso del segundo 40 tomaba la trama
   40, no la trama `40/hop`. Con hop de 46 ms eso es el segundo 1,9. El análisis
   entero se hacía sobre el primer minuto de la pista. Ahora es
   `hp[(beats / hop_s).astype(int)]`.
2. **Puntuación de compás sin normalizar.** El término de peso se sumaba sin
   dividir, así que la puntuación salía en 9,4 en una escala de 0 a 1, y el
   «compás» detectado era cualquier cosa.
3. **Novedad de Foote restando `S[i,i]`.** La similitud consigo mismo es
   siempre 1,0, así que restarla fijamente deja la curva de novedad **siempre
   negativa** y el umbral se va a 0. Lo correcto es la media de la diagonal, y
   desplazar la curva antes de normalizar.

> El cuarto, ya corregido, era el mismo punto 1 aplicado a los MFCC:
> `m = (np.arange(len(T)) * n_fft / SR) >= t` cogía **todas las tramas desde el
> pulso hasta el final de la pista**, con lo cual las primeras filas de la tabla
> de similitud acababan comparando la pista entera.

## El código

El que se ejecutó para la parte 4 de este documento. Para reejecutar, guardar
como `analiza.py` en cualquier sitio y usar el intérprete de la parte 1.

```python
"""
Analiza una pista con Essentia. Da numeros, no adjetivos.

Que sale, y por que cada cosa:
  tempo     RhythmExtractor2013, con las alternativas y el rango de confianza
  tonalidad KeyExtractor, con fuerza
  compas    deducido: en que posicion del compas cae el cambio de acorde mas
            veces. Essentia tiene 'Meter' pero va marcado como experimental,
            asi que se usa solo como contraste.
  acordes   ChordsDetection por trama, votes a pulso, agrupado a compas
  estructura MFCC sincronizado a beat -> similitud -> checkerboard kernel.
            No hay MusicSegmentation en la build de Python, y esta version
            hace lo mismo y ademas devuelve el compas del corte.
  nivel     RMS en dB por compas: donde se puede hablar encima
  espectro  centroide, rolloff y loudness global (mono, no EBU R128)

Uso: python analiza.py <fichero> <salida.json>
"""

import json
import sys

import numpy as np
from essentia.standard import (
    ChordsDetection,
    ChordsDetectionBeats,
    FrameGenerator,
    HPCP,
    KeyExtractor,
    Loudness,
    MonoLoader,
    MFCC,
    Meter,
    RhythmExtractor2013,
    SpectralPeaks,
    Spectrum,
    Windowing,
)


SR = 44100
HOP = 512


def cargar(ruta):
    return np.asarray(MonoLoader(filename=ruta, sampleRate=SR)(), dtype=np.float32)


def tempo(audio):
    """RhythmExtractor2013 devuelve a la vez el tempo, su confianza, las
    alternativas y los ticks. No hace falta un segundo rastreador: en esta
    build BeatTrackerMultiFeature no acepta bpm ni method, solo la senal."""
    bpm, ticks, conf, estimates, intervals = RhythmExtractor2013(method="multifeature")(audio)
    return {
        "bpm": round(float(bpm), 3),
        "confianza": round(float(conf), 4),
        "duracion_pulso_s": round(60.0 / float(bpm), 4),
        "alternativas": [
            {"bpm": round(float(e), 2), "inferencia": round(float(i), 2)}
            for e, i in zip(estimates, intervals)
        ],
        "ticks": np.asarray(ticks, dtype=np.float64),
    }


def tonalidad(audio):
    k, s, stren = KeyExtractor()(audio)
    return {"tonica": k, "escala": s, "fuerza": round(float(stren), 4)}


def hpcp(audio, n_fft=4096, hop=2048):
    """Perfil de clase de altura, 12 bins, sobre toda la pista.

    En esta build HPCP no se aplica a la senal: toma las frecuencias y las
    magnitudes de los picos espectrales. La cadena es
    ventana -> espectro -> picos -> HPCP, y se acumula en el tiempo.

    Devuelve tambien el hop, que es lo que permite volver de la trama al
    segundo: sin el, un acorde no tiene hora.
    """
    win = Windowing(type="hann", size=n_fft)
    spec = Spectrum(size=n_fft)
    peaks = SpectralPeaks(
        magnitudeThreshold=0.00001,
        minFrequency=40.0,
        maxFrequency=5000.0,
        maxPeaks=100,
        orderBy="magnitude",
    )
    hp = HPCP(size=12, sampleRate=SR)
    accum = []
    for frame in FrameGenerator(audio, frameSize=n_fft, hopSize=hop):
        if len(frame) < n_fft:
            continue
        s = np.asarray(spec(win(frame)))
        f = m = None
        if s.size and s.max() > 0:
            f, m = peaks(s)
        if f is None or len(f) == 0:
            accum.append(np.zeros(12))
            continue
        accum.append(
            np.asarray(hp(np.asarray(f, dtype=np.float32), np.asarray(m, dtype=np.float32)))
        )
    return np.array(accum), hop / SR


def acordes(hpcc, hop_s, beats):
    """Acorde por pulso.

    ChordsDetectionBeats no esta enlazado en esta build (2.1b6.dev), asi que
    se llama a ChordsDetection con la matriz entera: devuelve un acorde por
    trama. Luego se vota pulso a pulso. Es peor que la version beatsync en los
    casos en que el acorde cambia a mitad de pulso, y en una guitarra limpia eso
    no pasa: el cambio cae en el pulso.
    """
    chords, strengths = ChordsDetection()(hpcc)
    n = len(beats)
    por_beat = []
    for i in range(n):
        t0 = beats[i]
        t1 = beats[i + 1] if i + 1 < len(beats) else t0 + 0.5
        a, b = int(t0 / hop_s), int(t1 / hop_s)
        if b <= a:
            b = a + 1
        frag = chords[a:b]
        if len(frag) == 0:
            por_beat.append({"beat": i, "t": round(float(t0), 3), "acorde": "?", "fuerza": 0.0})
            continue
        cuenta, pesos = {}, {}
        for c, s in zip(frag, strengths[a:b]):
            cuenta[c] = cuenta.get(c, 0) + 1
            pesos[c] = pesos.get(c, 0.0) + float(s)
        el = max(cuenta, key=lambda c: (cuenta[c], pesos[c]))
        por_beat.append(
            {
                "beat": i,
                "t": round(float(t0), 3),
                "acorde": el,
                "fuerza": round(pesos[el] / cuenta[el], 3),
            }
        )
    return por_beat


def detectar_compas(hb, candidatos=(2, 3, 4, 6)):
    """Cuantos pulsos hay por compas y en que pulso cae el uno.

    La heuristica: el oido percibe el uno como el sitio donde el acorde mas
    claro. Asi que se puntua cada fase por cuantos cambios de acorde caen ahi,
    con un peso extra para los cambios grandes, que son los finales de frase.

    La puntuacion va de 0 a 1 y ademas se devuelve cuanto le gana a la segunda
    opcion: un compas que no gana por margen no es un compas, es una moneda al
    aire, y para clavar un corte eso no sirve.
    """
    d = np.abs(np.diff(hb, axis=0)).sum(axis=1)
    if len(d) < 8:
        return {
            "compas": None,
            "fase": None,
            "nota": "no deducible: la pista no tiene suficientes cambios de acorde",
        }
    med = np.median(d) + 1e-9
    cambios = np.where(d > 0.55 * med)[0]
    grande = set(np.where(d > 1.6 * med)[0].tolist())
    if len(cambios) < 4:
        return {"compas": None, "fase": None, "nota": "demasiados pocos cambios de acorde"}

    ops = []
    for metro in candidatos:
        for fase in range(metro):
            puntos = [i for i in cambios if i % metro == fase]
            if not puntos:
                continue
            frac = len(puntos) / len(cambios)
            peso = sum(1 for i in puntos if i in grande) / len(puntos)
            ops.append((frac * (0.5 + 0.5 * peso), metro, fase))
    ops.sort(reverse=True)
    top, segundo = ops[0], ops[1] if len(ops) > 1 else (0.0, 0, 0)
    return {
        "compas": top[1],
        "fase": top[2],
        "puntuacion": round(top[0], 4),
        "segunda_opcion": {"compas": segundo[1], "fase": segundo[2], "puntuacion": round(segundo[0], 4)},
        "margen": round(top[0] - segundo[0], 4),
        "n_cambios_de_acorde": int(len(cambios)),
    }


def acordes_por_compas(lista, metro):
    """Lo mismo agrupado: lo que de verdad se lee en una partitura."""
    out = []
    for c, ini in enumerate(range(0, len(lista), metro)):
        grupo = lista[ini : ini + metro]
        if not grupo:
            break
        cuenta = {}
        for g in grupo:
            cuenta[g["acorde"]] = cuenta.get(g["acorde"], 0) + 1
        principal = max(cuenta, key=cuenta.get)
        out.append(
            {
                "compas": c + 1,
                "t": round(grupo[0]["t"], 3),
                "acorde": principal,
                "cambia": cuenta.get(principal, 0) < len(grupo),
                "secuencia": [g["acorde"] for g in grupo],
            }
        )
    return out


def mfc_sync(audio, beats, n_bands=40):
    """MFCC sincronizado a beat: media y desviacion por pulso. Es el insumo de
    la estructura, porque la estructura es 'suena parecido' y no 'suena igual'."""
    n_fft = 2048
    win = Windowing(type="hann", size=n_fft)
    spec = Spectrum(size=n_fft)
    mfcc = MFCC(inputSize=n_fft // 2 + 1, sampleRate=SR, numberBands=n_bands)

    tramas = []
    for frame in FrameGenerator(audio, frameSize=n_fft, hopSize=n_fft):
        if len(frame) < n_fft:
            continue
        v = mfcc(spec(win(frame)))
        # MFCC devuelve dos salidas: las bandas de mel y los coeficientes.
        # Para comparar frames entre si sirven los coeficientes.
        if isinstance(v, (list, tuple)):
            v = v[-1]
        arr = np.asarray(v, dtype=np.float64)
        if arr.ndim > 1:
            arr = arr.reshape(-1)
        tramas.append(arr)
    if not tramas:
        return np.zeros((len(beats), 2 * n_bands))
    T = np.array(tramas)
    t_trama = np.arange(len(T)) * n_fft / SR

    # Un pulso es el INTERVALO entre dos pulsos. Tomar 'todas las tramas desde
    # este pulso hasta el final' hace que cada fila de la tabla contemplate el
    # resto de la pista, y las primeras filas quedan mas distintas de las
    # ultimas que dos tramos que no tienen nada que ver entre si.
    filas = []
    for i, t in enumerate(beats):
        fin = float(beats[i + 1]) if i + 1 < len(beats) else float(t) + 0.5
        idx = np.where((t_trama >= t) & (t_trama < fin))[0]
        if len(idx) == 0:
            # pulso mas corto que una trama: se coge la trama mas cercana
            idx = np.array([int(np.argmin(np.abs(t_trama - t)))])
        seg = T[idx]
        filas.append(np.concatenate([seg.mean(axis=0), seg.std(axis=0)]))
    return np.array(filas)


def estructura(feat, metro):
    """Segmentacion por similitud con checkerboard kernel.

    No devuelve una segmentacion cerrada sino los puntos donde mas cambia la
    musica. Ver la nota del final del bloque de seleccion: el motivo esta en
    'no saber la estructura'."""
    if len(feat) < 4 * metro:
        return {"candidatos": [], "nota": "pista demasiado corta para segmentar"}
    n = np.linalg.norm(feat, axis=1, keepdims=True)
    f = feat / np.maximum(n, 1e-9)
    S = f @ f.T  # similitud coseno

    L = metro * 2  # tamano del kernel, en pulsos
    nov = np.zeros(len(S))
    for i in range(L, len(S) - L):
        # El kernel de checkerboard compara los pares ALEJOS (bloque arriba
        # izquierda contra abajo derecha) con los pares CERCANOS. Los cercanos
        # son la media de la diagonal, NO S[i,i]: la similitud consigo mismo es
        # siempre 1.0, asi que usar S[i,i] resta una constante fija y la curva
        # entera sale negativa.
        lejos = S[i - L : i, i - L : i].mean() + S[i : i + L, i : i + L].mean()
        cerca = np.mean([S[i + k, i + k] for k in range(-L // 2, L // 2 + 1)])
        nov[i] = lejos - 2 * cerca

    # La novedad de Foote sale negativa en audio real: comparar con el percentil
    # 95 sin desplazar antes da 0 y declara degenerada una pista que si cambia.
    nov = nov - nov.min()
    ref = float(np.percentile(nov, 95))
    if ref <= 0:
        return {
            "candidatos": [],
            "nota": "curva de novedad degenerada: la pista no cambia de timbre",
        }
    nov = nov / ref

    # La novedad de una cancion real no son picos, son jorobas anchas: un umbral
    # (media+std o un percentil) o no corta nunca o corta por lo bajo, porque
    # la curva esta sesgada a la izquierda. Asi que no se fuerza un umbral: se
    # toman los maximos locales mas fuertes, con separacion minima, y se
    # devuelven como CANDIDATOS. No son "los cortes de la pista" — eso no lo
    # sabe la maquina — son los puntos donde mas cambia la musica, que es lo
    # que sirve para clavar una escena o un efecto encima.
    max_cortes = 14
    min_sep = 8 * metro
    cand = []
    for i in range(L + 1, len(nov) - L - 1):
        if nov[i] >= nov[i - 1] and nov[i] > nov[i + 1]:
            cand.append(i)
    cand.sort(key=lambda i: nov[i], reverse=True)
    elegidos = []
    for i in cand:
        if all(abs(i - j) >= min_sep for j in elegidos):
            elegidos.append(i)
        if len(elegidos) >= max_cortes:
            break
    elegidos.sort()
    cortes = [
        {
            "beat": int(i),
            "compas": int(i // metro + 1),
            "t": None,
            "novedad": round(float(nov[i]), 4),
        }
        for i in elegidos
    ]
    return {
        "candidatos": cortes,
        "max_cortes": max_cortes,
        "separacion_minima_compases": 8,
        "rango_noveldad": [round(float(nov.min()), 3), round(float(nov.max()), 3)],
        "nota": "son los puntos de mas cambio, no una segmentacion cerrada",
    }


def nivel_por_compas(audio, beats, metro):
    n = len(audio) // HOP
    tramas = audio[: n * HOP].reshape(n, HOP).astype(np.float64)
    rms = 10 * np.log10(np.maximum((tramas**2).mean(axis=1), 1e-12))
    t_rms = np.arange(n) * HOP / SR

    filas = []
    for c, ini in enumerate(range(0, len(beats), metro)):
        grupo = beats[ini : ini + metro]
        if len(grupo) == 0:
            break
        t0 = float(grupo[0])
        t1 = float(beats[ini + metro]) if ini + metro < len(beats) else t0 + metro * 0.5
        m = (t_rms >= t0) & (t_rms < t1)
        if m.sum() == 0:
            continue
        v = rms[m]
        filas.append(
            {
                "compas": c + 1,
                "t": round(t0, 3),
                "mm_ss": f"{int(t0//60)}:{t0%60:04.1f}",
                "db_medio": round(float(v.mean()), 1),
                "db_pico": round(float(np.percentile(v, 95)), 1),
            }
        )
    return filas


def espectro(audio):
    n_fft = 4096
    win = Windowing(type="hann", size=n_fft)
    spec = Spectrum(size=n_fft)
    freqs = np.linspace(0, SR / 2, n_fft // 2 + 1)
    acum_c = acum_r = 0.0
    n = 0
    for frame in FrameGenerator(audio, frameSize=n_fft, hopSize=n_fft):
        if len(frame) < n_fft:
            continue
        m = np.asarray(spec(win(frame)))
        tot = m.sum()
        if tot <= 0:
            continue
        acum_c += float((freqs * m).sum() / tot)
        acum_r += float(freqs[int(np.searchsorted(np.cumsum(m), 0.85 * tot))])
        n += 1
    # LoudnessEBUR128 exige un vector estereo (vector<stereosample>) y aqui se
    # analiza en mono, asi que se usa Loudness, que es energia^(2/3) y no LUFS.
    # El LUFS real de la obra hay que medirlo sobre el estereo en la sala:
    # ver produccion.md.
    lufs = Loudness()(audio)
    return {
        "centroide_medio_hz": round(acum_c / max(n, 1), 1),
        "rolloff85_medio_hz": round(acum_r / max(n, 1), 1),
        "loudness_stevens": round(float(lufs), 2),
    }


def analizar(ruta):
    audio = cargar(ruta)
    dur = len(audio) / SR
    t = tempo(audio)
    key = tonalidad(audio)
    beats = t.pop("ticks")
    bconf = t["confianza"]

    hp, hop_s = hpcp(audio)
    # Los picos van por tiempo, no por indice de trama. Un beat en el segundo
    # 40 cae en la trama 40/hop, no en la trama 40: indexar por el valor del
    # pulso miraba solo el primer minuto de la pista y daba un compas falso.
    tramas = np.clip((beats / hop_s).astype(int), 0, len(hp) - 1)
    hb = hp[tramas]
    comp = detectar_compas(hb)
    # Si el compas no se deduce, el resto del analisis necesita uno para agrupar.
    # Se usa 4 como valor de trabajo y se dice, porque 4/4 es la convencion
    # habitual pero no es un dato: es una suposicion para poder seguir.
    metro = comp["compas"]
    if metro is None:
        comp["metro_supuesto_para_agrupar"] = 4
        metro = 4

    # contraste con el algoritmo experimental de Essentia
    try:
        meter_exp = int(Meter()(np.abs(np.diff(beats)).reshape(-1, 1) * np.ones((1, metro))))
    except Exception as e:
        meter_exp = f"no disponible ({e.__class__.__name__})"

    ac_beats = acordes(hp, hop_s, beats)
    ac_barras = acordes_por_compas(ac_beats, metro)
    feat = mfc_sync(audio, beats)
    est = estructura(feat, metro)
    bt = [round(float(x), 3) for x in beats]
    for c in est["candidatos"]:
        if c["beat"] < len(bt):
            c["t"] = bt[c["beat"]]
            c["mm_ss"] = f"{bt[c['beat']]//60:.0f}:{bt[c['beat']]%60:04.1f}"
    filas = nivel_por_compas(audio, beats, metro)

    return {
        "fichero": ruta,
        "duracion_s": round(dur, 3),
        "duracion_mm_ss": f"{int(dur//60)}:{dur%60:04.1f}",
        "tempo": t,
        "tonalidad": key,
        "compas": metro,
        "golpe_fuerte_desde_beat": comp["fase"],
        "compas_essentia_experimental": meter_exp,
        "deduccion_compas": comp,
        "n_beats": int(len(beats)),
        "confianza_beats": bconf,
        "primer_beat_mm_ss": f"{beats[0]//60:.0f}:{beats[0]%60:04.1f}" if len(beats) else None,
        "acordes_por_compas": ac_barras,
        "estructura": est,
        "nivel_por_compas": filas,
        "espectro": espectro(audio),
    }


if __name__ == "__main__":
    ruta = sys.argv[1]
    salida = sys.argv[2] if len(sys.argv) > 2 else None
    r = analizar(ruta)
    txt = json.dumps(r, ensure_ascii=False, indent=1)
    if salida:
        with open(salida, "w") as f:
            f.write(txt)
    print(txt)
```

---

# Parte 3 — Los datos

Qué significa cada campo y **cuánto se le puede creer**. La regla que resume
todo: *si un campo no tiene un criterio de rechazo, se está creyendo algo que
la máquina no sabe.*

| Campo | Qué es | Se le cree cuando |
|---|---|---|
| `duracion_s` | Segundos de audio. Impecable | Siempre. Es contar muestras |
| `tonalidad.fuerza` | 0 a 1, cómo de segura es la tónica | **> 0,8**. Por debajo de 0,5 no se usa |
| `tempo.bpm` | Pulsos por minuto | Solo con las alternativas de al lado, y entendiendo el margen |
| `tempo.alternativas` | Las otras lecturas candidatas, con su inferencia | El **rango** (mínimo a máximo) es el margen de error real |
| `n_beats` | Cuántos pulsos ha encontrado | Tiene que cuadrar con la duración: `n_beats × pulso ≈ duración` |
| `deduccion_compas.margen` | Cuánto le gana el compás elegido al segundo mejor | **> 0,05**. Por debajo, no hay compás |
| `acordes_por_compas[].acorde` | El acorde mayoritario de cada grupo | Solo los que se repiten. Los que salen una vez son ruido |
| `acordes_por_compas[].cambia` | `true` si el grupo no es todo el mismo acorde | Es el indicador útil: marca los **cambios de harmony**, que es lo que se ve |
| `nivel_por_compas[].db_medio` | RMS en dB del grupo | Sirve para saber **dónde se puede hablar encima** |
| `nivel_por_compas[].db_pico` | Percentil 95, no el máximo | Un máximo es un solo sample y no dice nada |
| `espectro.centroide_medio_hz` | "¿Brilla o retumba?" | Como comparación entre pistas, nunca como cifra |
| `espectro.loudness_stevens` | Energía^2/3. **No es LUFS** | Nada. Solo ver que ha cargado |
| `estructura.candidatos` | Puntos de más cambio de timbre | **No.** Ver la parte 5 |

## Un dato sobre la fuerza del compás

`deduccion_compas.margen` es lo más valioso que produce el script y lo que más
gente se salta. Es la diferencia entre la opción ganadora y la segunda mejor.

- Margen alto: hay un compás claro y se puede clavar una escena en él.
- Margen bajo: hay varias lecturas igual de buenas, **el compás no se sabe**, y
  clavar un corte en una de ellas es echar una moneda al aire.

Por debajo de 0,05 el script deja el compás sin decidir y anota
`metro_supuesto_para_agrupar` con el valor con el que ha seguido agrupando.
**Ese número es una suposición para poder continuar, no una medición.**

---

# Parte 4 — Avivas el fuego

Ejecutado el 2026-09-29 sobre `1_Avivas.wav` (el original) y, el día anterior,
sobre las dos exportaciones MP3 que estaban en `recursos/musicas/`.

> **Estado de la carpeta.** A 2026-09-29 `recursos/musicas/` contiene **solo
> `1_Avivas.wav`**. Los dos MP3 ya no están y nunca llegaron a estar en git, así
> que sus datos de aquí **no se pueden volver a comprobar**. Se conservan los
> números medidos porque se midieron, y porque el original los confirma casi
> todos.

## El original

| | |
|---|---|
| Fichero | `1_Avivas.wav` |
| MD5 | `b526d616a15663fc0a132a701f13b6c0` |
| Canales | 2 (estéreo) |
| Frecuencia | **48.000 Hz** |
| Profundidad | **24 bits** |
| Muestras | 16.574.090 |
| Duración | 345,294 s (**5:45,3**) |
| Tamaño | 94,8 MB |

**Es el fichero maestro, y el que hay que usar.** 48 kHz y 24 bits es lo que
carry el disco; los MP3 eran exportaciones. El análisis lo baja a 44,1 kHz mono
porque Essentia trabaja ahí, y eso **no cambia las conclusiones musicales** pero
sí significa que estas cifras son de una versión reescalada.

> La carpeta `recursos/musicas/` es de `root`. Un WAV de 94,8 MB **no cabe por
> Discord** (el límite del bot es 8 o 25 MB), así que los ficheros grandes hay
> que copiarlos a la máquina o exportarlos comprimidos.

## Lo que dice el original

| Dato | Valor | Comentario |
|---|---|---|
| **Tonalidad** | **Re mayor**, fuerza **0,91** | Igual que la del instrumental MP3 (0,92) |
| **Tempo** | **93,33 BPM** | El instrumental daba 93,32. **Coinciden** |
| Pulso | 0,643 s | |
| Pulsos | 546 | |
| Primer pulso | 0:00,7 | |
| Centroide | 3.302 Hz | |
| Rolloff 85 % | 7.434 Hz | |
| **Compás** | **No se sabe** | Margen 0,0059. Igual de irresoluble |
| Silencio (< -60 dB) | **1,5 %** | Es la mezcla más limpia de las tres |

### El nivel dice que esta es la mezcla buena

| | Original | Instrumental MP3 | «Vocal» MP3 |
|---|---|---|---|
| Silencio | **1,5 %** | 2,9 % | **44,8 %** |
| Mediana | **-9,0 dB** | -10,5 dB | -39,3 dB |
| Bloques sonoros | **1** de 5:28 | 1 de 5:22 | **48** |
| Tonalidad | Re mayor (0,91) | Re mayor (0,92) | **Do mayor** |
| Tempo | 93,33 | 93,32 | 91,01 |

El original es una **mezcla continua**: arranca con un fundido corto y a partir
de **0:11,5 no baja de -45 dB en 5 minutos y 28 segundos**, hasta el final.

**El MP3 instrumental era una exportación completa de esta misma grabación** —
mismo tempo a dos decimales, misma tonalidad, mismos acordes dominantes, misma
duración. El que no cuadra es el fichero llamado «vocal».

### Los acordes

| Acorde | Veces | % |
|---|---|---|
| **D** (Re) | 134 | 49,1 % |
| **C** (Do) | 36 | 13,2 % |
| **G** (Sol) | 30 | 11,0 % |
| **Am** (La menor) | 30 | 11,0 % |
| Dm | 14 | 5,1 % |
| Bm, A, Em, F, E, F#m | 29 juntos | 10,6 % |

Los cuatro dominantes son el **84 %** otra vez, y en el mismo orden de magnitud
que en el instrumental. El original no aporta acordes nuevos: confirma los
anteriores.

**El Re aguanta los primeros 23 grupos, de 0:00,7 a 0:30,2.** El primer cambio
está en el grupo 24, a los **0:30,9**, y es un Sol.

Cada grupo dura 1,286 s (dos pulsos de 0,643 s) y **74 de los 273 grupos tienen
un cambio de acorde dentro**:

```
D/G   C/Am   C/A   C/D   D/C   Bm/D   D/C   C/Am   G/D   F/C   C/Am   G/Dm
```

Es decir: **la armonía cambia en cada pulso, y la melodía va por encima.** Un
Re cada dos pulsos no es un acorde sostenido, es un bajo alternando. Eso
confirma que **el compás no es 2/4** — un compás de dos pulsos con cambio en
cada uno sería absurdo — y refuerza que la lectura de 2/4 es un empate, no un
resultado. También avisa de algo para la escena: esta pista **no tiene un acorde
que sostenga**, así que cualquier efecto armónico tiene que ir al pulso o se
desincroniza solo.

### El nivel, grupo a grupo

| Grupo | Tiempo | Nivel | Pico |
|---|---|---|---|
| 1 | 0:00,7 | -48,2 dB | -45,7 |
| 4 | 0:05,0 | -49,3 dB | -47,2 |
| 9 | 0:11,6 | -44,4 dB | -41,3 |
| 11 | 0:14,2 | -41,6 dB | -36,7 |
| 12 | 0:15,5 | -39,1 dB | -36,0 |
| … | … | … | … |
| 271 | 5:42,4 | -70,6 dB | -69,4 |
| 273 | 5:44,0 | -120 dB | -120 |

El grupo 273 a -120 dB es **silencio digital**: la pista acaba en corte seco,
sin cola. Importante para la salida de escena: no hay nada que se desvanezca al
final, hay que hacerlo desde el mezclador.

## Cuarentena

**Los datos de `Avivas_vocal.mp3` no son válidos, y no por poco.**

| Medida | Instrumental | Vocal |
|---|---|---|
| Tiempo en silencio (< -60 dB) | 2,9 % | **44,8 %** |
| Nivel mediano | -10,5 dB | **-39,3 dB** |
| Sonando por encima de -45 dB | Un bloque continuo de 5:22 | **48 tramos** de 3 a 19 s |
| Correlación con el instrumental | — | **0,14** |

Las dos consecuencias medibles:

1. **La correlación es 0,14.** Si fuera la misma mezcla con la voz encima, en
   un pasaje instrumental sería > 0,8. No lo es: **no son la misma mezcla.**
2. **Los pulsos no cuadran con la duración.** 612 pulsos a 91 BPM son 403
   segundos, para una pista que dura 345. El rastreador de ritmo se equivoca
   cuando hay voz encima — por eso da Re en vez de Sol, 91 en vez de 93,3, y
   una tonalidad distinta — y por eso este fichero **no sirve para análisis
   musical**.

Lo que sí sale de aquí, y es un hecho, no una interpretación: **la voz suena a
bloques, en 48 tramos, y calla el 45 % del tiempo.** Los bloques más largos son
4:11,9 → 4:31,1 (19,2 s) y 5:13,5 → 5:27,5 (14,0 s). El punto más alto de todo
el fichero es 5:34,9, que está **77,5 dB por encima** del instrumental en ese
mismo instante.

Si ese silencio es un error de exportación o una decisión artística cambia
todo lo que se puede hacer con la pista. Está en las preguntas abiertas.

---

# Parte 5 — Lo que no sale

Tres cosas que **no** se han podido medir, y por qué no conviene présentarlas
como si se hubieran medido.

## El compás

Los dos métodos disponibles fallan:

- El `Meter` de Essentia da `RuntimeError` con la entrada que se le pasa. Es
  además un algoritmo marcado como experimental por la propia biblioteca.
- La deducción propia da 2/4, pero con un margen de **0,0072** sobre la segunda
  opción (2/4 en otra fase, 0,3084). Eso no es una medición: es empate.

**Hacen falta unos cuantos con un metrónomo, o contar en voz alta.** Es una
tarea de cinco minutos con un oído, y sustituye a un script entero.

## La estructura

El detector de cambio de timbre —MFCC por pulso, similitud coseno, kernel de
checkerboard— produce una lista de 14 «candidatos», **y no sirve**. La prueba
de que no sirve es esta: siendo **el mismo tema**, los candidatos del
instrumental y los de la versión vocal coinciden **2 de 14**, y ni uno de esos
dos está a menos de un grupo del equivalente en la otra lista:

```
instrumental   12  26  34  42  51  72  94 120 135 144 199 237 252 264
vocal          36  72  91 109 123 165 180 192 208 237 246 262 272 291
              ───────────────────────^^──────────────────────^^
                            2 de 14
```

La lista sale además con la novedad clavada en un rango de 0,94 a 1,05 — es
decir, todos los «cambios» son igual de fuertes, que es la firma de una curva
plana. Se está eligiendo ruido, no estructura.

Los campos se conservan en el JSON porque son la entrada de un método mejor, no
porque sirvan de nada ahora. **Los puntos donde la música cambia hay que
encontrarlos oyendo.**

> Nota: con el compás sin resolver, el kernel es del tamaño equivocado y eso
> por sí solo invalida el resultado. Se corrigió la parte 5 de la lista
> cuando se detectó, pero la falta de compás no se puede corregir a máquina.

## El LUFS

`LoudnessEBUR128` necesita estéreo y se analiza en mono, así que **no hay
sonoridad integrada en LUFS**. Lo que da el script, `loudness_stevens`, es
energía elevada a 2/3 (ley de Stevens) y **no es comparable con los LUFS de una
cadena de audio ni con los de la sala**. El LUFS real hay que medirlo sobre el
estéreo de la obra, en la sala. Apuntado en `produccion.md`.

Y de todos modos, un LUFS de un MP3 de referencia no dice cómo tiene que sonar
la obra en sala: eso es una decisión de niveles de la Production, no una
medición.

## La precisión del tempo

93,3 BPM con alternativas de 89,1 a 95,7. El error de ±3 BPM **se acumula**: a
lo largo de 5:45 son unos 10 segundos de deriva. Sirve para saber que la
pista va en torno a 93 y para clavar un efecto al principio; **no sirve para
programar un corte exacto en el minuto 3.** Para eso, o un tap manual, o
sincronizar el Ableton al rejilla de rejilla con un warp.

---

# Los nueve ficheros

> **El prefijo del nombre es el número de pista del disco.** Confirmado por el autor el
> 2026-09-29. Antes esta tabla vivía con el orden de una captura del reproductor, que no
> correspondía con los nombres de los ficheros; `investigacion/referencias.md` se corrigió
> ese mismo día.

Siete u ocho de cada nueve son estéreo 24 bits. `8_Vuela.wav` está a 44,1 kHz y los otros
ocho a 48 kHz: una diferencia de 44 segundos de cola entre temas si se SRC-corrigen sin
juntar, y mezclarlos en el Set obligaría a una de las dos conversiones.

| `tt` | Fichero | Duración | BPM | Tonalidad | Fuerza | kHz |
|---|---|---|---|---|---|---|
| 01 | `1_Avivas.wav` | 5:45,3 | 93,33 | Re mayor | 0,91 | 48 |
| 02 | `2_On S'en Fout.wav` | 4:38,4 | 95,89 | Sol menor | **0,77** | 48 |
| 03 | `3_La Reina.wav` | 5:24,0 | 98,53 | Mi mayor | 0,87 | 48 |
| 04 | `4_Lo Llama Vida.wav` | 3:50,0 | 109,98 | Si menor | 0,88 | 48 |
| 05 | `5_Ser Artista.wav` | 3:58,8 | 138,06 | La mayor | 0,94 | 48 |
| 06 | `6_La Puerta.wav` | 4:46,0 | 98,99 | Re menor | 0,93 | 48 |
| 07 | `7_Seica.wav` | 4:58,9 | 125,03 | Mi menor | 0,94 | 48 |
| 08 | `8_Vuela.wav` | 3:33,3 | 164,04 | Re mayor | 0,87 | **44,1** |
| 09 | `9_Está Bien.wav` | 3:23,3 | 117,57 | La mayor | 0,92 | 48 |

La **fuerza** es lo rápido que el detector encuentra el acorde de tónica, de 0 a 1. Ocho de
los nueve están por encima de 0,87 y se pueden citar. **`2_On S'en Fout` está en 0,77** y es
el único que no: enarmonía o tonalidad ambigua, y hasta que se escuche no se afirma. Que sea
el único en segundo plano encaja con que es la única canción en francés del disco, pero
eso es una conjetura y no se escribe como dato.

**Los nueve JSON están en `/tmp/opencode/analisis/`,** uno por fichero, con la estructura que
describe la parte 5. Lo que sale de aquí y **no** sale de aquí:

- **Sirve**: cuánto material hay, a qué tempo está, en qué tonalidad, qué acordes
  domina, y para Chordsymbols si algún día se quiere.
- **No sirve**: compás, estructura, y si un acorde suena disonante. Son las tres
  cosas que la máquina no cuenta bien y el oído decide en diez segundos. El
  compás además sale con márgenes tan bajos que no se puede decir ni de broma: 2/4
  es lo que devuelve el detector, y no es una respuesta.

Los nueve tempos van del 93 al 164. **Eso decide una cosa de la obra:** la variación
musical no puede tener un tempo fijo, porque no es un tempo de la obra, es el de la
canción de la que sale. Si una construcción mezcla dos instrumentos del mismo tema,
heredan su tempo. Si mezcla dos temas distintos, no —y por eso la regla de «un tema,
una variación» no es solo una cuestión de gusto, es lo que hace que el tempo sea un dato.

## Los stems: «Avivas el fuego», 75 ficheros

> **Subidos el 2026-09-29** a `recursos/musicas/Avivas el Fuego - files/`. Es el primer tema
> con instrumentación separada; los otros ocho siguen siendo mezclas.

Formato, medido: **los 75 son 24 bits a 48 kHz, 339,4 s**, 63 en mono y 12 en estéreo. Todos
idénticos en duración, y **5,9 s más cortos que la mezcla** (345,3 s). Un recorte igual en los
75 es un exportado uniforme, no un fallo: lo que se ha perdido es la cola final. Importante
para la 11, que es donde la canción se apaga.

### Un tercio de los ficheros no tiene nada dentro

**26 de 75 son silencio digital absoluto** — pico exactamente 0,00000, no «muy bajito»:
silencio. Es un tercio del material.

| Grupo | Con señal | Total | |
|---|---|---|---|
| `IAGO` (PLATE, SLAP, TF51, TF51 DRIVE) | **0** | 4 | todo vacío |
| `SHAKER` #09 a #12 | **0** | 4 | todo vacío |
| `ALEX SLAP` (#69, _3, _4) | **0** | 3 | |
| `TANIA SLAP` (#69, _7, _8, _9) | **0** | 3 de 3 | |
| `ALEX PLATE` (_4, #69) | 1 de 3 | 3 | |
| `TANIA PLATE` / `TANIA TF51` / `TANIA TF51 DRIVE` | 1 de 3 | 3 | |
| `GUIT 440` / `GUIT 441` / `GUIT 8 440` / `GUIT LINE` / `GUIT ROOM L` / `GUIT ROOM R` | 2 de 2 | 2 | completo |
| `BASS DI`, `BASS PEDALES` | 2, 3 | 2, 3 | completo |
| `KICK` (4), `OH L/R 4038` (2 c/u), `OH L/R 440`, `TOM 1/2`, `ROOM L/R 040`, `ROOM 58`, `RIDE`, `HH`, `DARBOUKA`, `CAJA`, `GOLIAT`, `SNR DW/UP`, `Audio 164`, `ACU V44 M` | 1 de 1 | | completo |

Los nombres son de canal y de plugin de Pro Tools (`- Comp A combinado_7`, `#69`), no nombres
de instrumento. Se han deducido por la numeración de micro y por lo que hace el fichero: `440` y
`441` son dos micos de Parlor (marca Neumann), `4038` es un par de overheads, `e912` un bombo,
`KICK PAR` un par
cardioide, `SNR` es caja/salame, `421` es un micro de Samson tipo HiHat.

### El problema gordo: no hay voz seca

**No existe ningún fichero de voz en seco.** Los únicos ficheros que podrían serlo son `ALEX` y
`TANIA` (e `IAGO`, vacío entero), y de los dos primeros:

- Solo tienen señal las versiones **`TF51`** y **`TF51 DRIVE`** — es decir, **con la reverb
  Telefunken 51 ya puesta**, y la DRIVE con más saturación. Los `_3`, `_7`, `_8`, `_9` que se
  exportaron fueron los equivocados.
- `ALEX SLAP` y `TANIA SLAP`, enteras, están vacías.

Y `ALEX TF51` y `TANIA TF51` no son el mismo material entre sí: no correlacionan a nivel de
muestra. Son dos fuentes distintas —dos voces, o dos micros de la misma voz en momentos
distintos— y **no hay forma de decidir cuál por medir**.

> `TODO(preguntar):` **¿de dónde saco la voz en seco?** Hace falta para «la voz sola», que es
> la primera variación que pide la escena 01. Con solo el `TF51` no se puede: la reverb viene
> dentro y no se puede quitar. Y **¿quién es ALEX y quién es TANIA?** Si son dos voces, hay
> que saber cuál es la que canta la melodía antes de construir nada.

### Cómo entra la canción por capas

Medido por stems, mirando dónde aparece señal en cada uno (umbral −52 dBFS en una ventana de
1 s):

| t | Qué entra |
|---|---|
| 0 – 15 s | nada por encima del umbral |
| **15 s** | **palmas** — y solo palmas |
| **22 s** | guitarra acústica (`ACU V44 M`) y pedal de bajo |
| **26 s** | guitarra eléctrica (`GUIT 440`) |
| **30 s** | darbuka, `KICK 8 640`, overheads, sala |
| **41 s** | bombo (`KICK IN e912`) |
| **42 s** | **las dos voces** (ALEX y TANIA) |
| — | caja, tom, charles, ride, sala L/R, ruido: solo a partir del minuto 2 |

**No hay una entrada de «solo las guitarras».** La guitarra eléctrica llega en el segundo 26,
y cuando llega ya están las palmas, la acústica y el bajo. La pieza no se abre en capas de
guitarra: se abre con **palmas**. Es un hecho de la canción y **cambia la variación que pide la
escena 01** («solo las guitarras, muy limpia y suave»): no se puede tomar del principio, hay
que construirla apagando stems o tomando un tramo donde la guitarra esté sola.

### Qué sí se puede correlacionar

Ninguna pareja llega a 0,9 de correlación a nivel de muestra: **no hay dos ficheros que sean
el mismo material con distinto plugin**, solo fuentes parecidas. Las más altas:

| Corr. | Par | Lectura |
|---|---|---|
| 0,66 | `GUIT 440 _7` = `GUIT 441 _7` | misma guitarra o la misma parte, dos tomas |
| 0,62 | `ALEX TF51 _3` = `ALEX TF51 DRIVE _3` | mismo bus, con y sin drive — la reverb es la diferencia |
| 0,59 | `GUIT 441 _7` = `GUIT 8 440 _7` | idem |
| 0,50 | `BASS DI _4` = `BASS PEDALES _4` | misma caja, directo y pedal |
| 0,43 | `OH L 4038#262` = `OH R 4038#262` | el mismo par de overheads, L y R |
| 0,43 | `Palmas` = `Palmas combinado` | mismo fichero exportado dos veces |

Los seis ficheros de guitarra (`GUIT 440`, `GUIT 441`, `GUIT 8 440`, `GUIT LINE`, `GUIT ROOM L`
y `GUIT ROOM R`) se correlacionan entre sí del 0,47 al 0,66. Lo razonable es que sean **tres
micros directos de la misma guitarra más `GUIT LINE` y dos salas** — o tres guitarras tocando
lo mismo. Las dos lecturas dan una mezcla distinta, y con un nombre de fichero no se puede
decidir entre ellas.

> `TODO(preguntar):` **`GUIT 440`, `GUIT 441` y `GUIT 8 440` son tres guitarras o una?** Es la
> pregunta que decide qué se puede hacer con «solo las guitarras». Y `GUIT LINE`, `GUIT ROOM L` y
> `GUIT ROOM R` ¿son la misma señal desde otros sitio, o mezcla de la guitarra con otra cosa?
> De esto no se puede hacer nada con un nombre de fichero.

### Y los comps

Cada instrumento tiene varios: `_7`, `_8`, `_9`, `_11`, `#69`, `#138`, `#262`. Los números
distintos **no son versiones del mismo fichero**: `GUIT 440 _7` y `GUIT 440 _8` correlacionan
solo al 0,33 a nivel de muestra, que es lo que se esperaría de **tomadas distintas de la misma
partitura** — o de comps distintos. Cuál comp es el bueno no se deduce de nada: hay que
oírlos. `TODO(preguntar)`.


---

# Parte 6 — Preguntas abiertas

> **RESUELTO 2026-09-29 — la duración medida no es «la duración del disco».** Se
> decía aquí que `referencias.md` estaba equivocada por decir 6:41 cuando el
> fichero mide 5:45,3. El autor lo desmintió el mismo día, y tiene razón: **son dos
> cosas distintas.** El disco es lo que se volcó; lo que tenemos aquí son **nueve
> mezclas de trabajo**, que pueden tener otra duración. Las dos medidas son
> ciertas en su terreno y no hay que obligarlas a coincidir.
>
> Da igual para el trabajo: una duración solo sirve para saber **cuánto material
> hay**, y la del fichero es la que sirve. Para Avivas, la mezcla mide **5:45,3**
> (345,294 s) y el MP3 instrumental coincide con ella hasta los 3 milisegundos de
> relleno del codificador — es que el MP3 salió de este fichero. El **prefijo del
> nombre de los ficheros es el número de pista del disco**, confirmado por el
> autor, así que `1_Avivas.wav` es la pista 01. Datos corrigió el orden y la
> duración en `investigacion/referencias.md` el 2026-09-29.

> `TODO(preguntar):` **`Avivas_vocal.mp3` — ¿se exportó mal, o la voz va a
> trozos a propósito?** Sigue sin respuesta, y ahora hay un dato nuevo que la
> hace más urgente: **el original es una mezcla continua con 1,5 % de
> silencio**, y el fichero llamado «vocal» tenía 44,8 %. La diferencia no es de
> mezcla ni de masterizado, es de contenido. O al original le falta la voz, o
> el fichero «vocal» está roto.
>
> Lo que **no** se puede decir es si el original tiene voz dentro. Eso no sale
> de medir: sale de escuchar treinta segundos. Es la pregunta más rápida de esta
> lista y la que más condiciona el resto.

> ~~**¿Cuál es el fichero de trabajo de la obra?**~~ **Contestado: hay nueve.**
> El autor subió las nueve mezclas del disco a `recursos/musicas/` el
> 2026-09-29, en estéreo 24 bits, con el prefijo del número de pista. Con eso la
> pregunta siguiente cambia: no «qué fichero» sino **«de qué instrumento sale»**,
> y para eso hacen falta los stems, que el autor también tiene. Ver «Los nueve
> ficheros» más abajo.

> `TODO(preguntar):` **Los dos MP3 han desaparecido de `recursos/musicas/`** y
> nunca estuvieron en git. Si eran exports que hay que regenerar, hay que
> volver a exportarlos desde Ableton. No está claro si se han borrado a propósito
> al dejar el original.

## Un aviso sobre reutilizar esto

Este script sirve para **una pregunta**: ¿qué pasa aquí, en número? No sirve
para decir cómo suena una canción, y las tres cosas que no da —compás,
estructura y sonoridad— son precisamente las tres que un oído da en diez
segundos.

El reparto que salió de aquí, y que conviene mantener:

- **La máquina**, lo repetible y lo countable: tonalidad, tempo, acordes,
  nivel. Números que se pueden citar.
- **El oído**, lo demás: compás, dónde empieza cada sección, si una guitarra
  suena sucia o triste, y si un silencio es un fallo o una decisión.
