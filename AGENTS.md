# Netta Rufina — obra de teatro de objetos y títeres

Proyecto de una obra teatral de objetos y títeres creada a partir de un disco de la banda
Netta Rufina. Este directorio contiene el guion y los recursos de la obra, en construcción.

**Fase inicial: la premisa todavía no está cerrada.** No hay argumento, reparto, formato de
escena ni duración decididos. No des por sentado nada que no esté escrito en estos ficheros:
si una decisión se tomó en una conversación y no llegó al disco, no existe.

## La regla más importante

**No inventes datos sobre la banda, el disco o las canciones.** Todo lo que se afirme sobre
Netta Rufina tiene que ser verificable o estar marcado como pendiente.

- Si necesitas un dato (tracklist, créditos, autoría de las letras, biografía, componentes) y
  no está ya en `investigacion/referencias.md`, **pregunta**. No lo deduzcas ni lo rellenes de
  memoria: una referencia falsa en un guion se propaga a todo lo demás.
- Cuando falte un dato, escribe `TODO(preguntar):` en el fichero en vez de inventarlo. Queda
  visible para la siguiente sesión y para el autor.
- Separa siempre lo verificado de lo supuesto. `investigacion/referencias.md` lleva las
  fuentes; los guiones llevan la obra, no los datos.

**Las letras de las canciones se pueden citar.** El autor del proyecto es miembro de Netta
Rufina con derechos de autor sobre las canciones, así que las letras no están protegidas frente
a él: pueden aparecer en estos ficheros, completas o en fragmentos, cuando la escena las necesite.
Lo que sí sigue en pie:

- **No inventes letra.** Si un verso no está en las fuentes (`investigacion/referencias.md`) o
  no lo aporta el autor, se marca `TODO(preguntar):` o se parafrasea. Inventar una línea que
  parece real y no lo es es peor que dejarla fuera.
- **Un fragmento se cita, no se vuelca.** Cuando la escena usa la letra como imagen (un cartel,
  una voz en off, un objeto), lo natural es citar la línea que se ve o se oye, no volcar la
  canción entera en el libreto.
- **Gallego y francés.** Se citan en su idioma y se glosan al español.
- Para una representación pública sigue habiendo que resolver la parte administrativa con la
  entidad de derechos — anotado en `recursos/produccion.md`.

## Idioma

Todo el material en español. Cuando una canción o una expresión quede en su idioma original
(gallego, francés), se cita tal cual y se glosa al español.

## Estructura de ficheros

```
netta/
├── AGENTS.md                      este documento
├── README.md                      índice y estado del proyecto
├── guion/
│   ├── sinopsis.md                la obra en un párrafo; la brújula
│   ├── escaleta.md                ESQUELETO: qué ocurre en cada escena
│   └── libreto/                   EL TEXTO, un fichero por escena
│       ├── 01-el-latido.md
│       ├── 02-la-infancia.md
│       ├── 03-el-sombrerero.md
│       ├── 04-la-rutina-en-bucle.md
│       ├── 05-el-tiro-al-blanco.md
│       ├── 06-la-reina.md
│       ├── 07-la-salida-que-no-esta.md
│       ├── 08-la-nina-triste-y-el-ventilador.md
│       ├── 09-la-senal.md
│       ├── 10-lo-ancestral.md
│       ├── 11-el-fuego.md
│       └── 12-cuerda-floja.md
├── recursos/
│   ├── sonido.md                  todo el sonido de la obra, en Ableton Live
│   ├── fichas.md                  personajes, objetos y títeres uno a uno
│   ├── escena.md                  puesta en escena, manipulación, técnica
│   └── produccion.md              calendario, presupuesto, derechos
└── investigacion/
    └── referencias.md             datos verificados sobre banda y disco, con fuente
```

## Para qué sirve cada fichero

- **`guion/sinopsis.md`** — el norte. Si una escena nueva no encaja con la sinopsis, o
  cambia la sinopsis, se actualiza aquí primero.
- **`guion/escaleta.md`** — el índice y el estado de avance. Una línea por escena, con su
  estado. Es lo primero que se lee y lo primero que se actualiza. Una escena pasa por:
  `idea` → `boceto` → `revisada` → `cerrada`.
- **`guion/libreto/`** — el texto en sí, con las acotaciones, **un fichero por escena**
  (`NN-nombre.md`, dos dígitos, minúsculas, guiones). Se escribe cuando la escena ya está
  `revisada` en la escaleta; no se escribe a la vez. Ver «Un fichero por escena» más abajo.
- **`recursos/sonido.md`** — todo el sonido de la obra. La música del disco (qué pista en qué
  momento y por qué suena ahí) **y los efectos sonoros**, con la descripción de cómo se hacen
  en Ableton Live. Ver «El sonido» más abajo.
- **`recursos/fichas.md`** — una entrada por personaje, objeto o títere: qué es, qué quiere,
  cómo se manipula, de qué está hecho.
- **`recursos/escena.md`** — espacio, ritmo, transiciones, cómo se ve lo que no se oye y al
  revés.
- **`recursos/produccion.md`** — lo que hay que resolver para que la obra exista fuera del
  papel: fechas, sala, personas, dinero, derechos.
- **`investigacion/referencias.md`** — lo único donde se anotan datos de la banda y el disco,
  siempre con su fuente.

## Flujo de trabajo

1. Antes de escribir, mira `guion/escaleta.md` para saber dónde está la obra.
2. Trabaja **una escena por sesión**. Es un proyecto creativo, no una tarea lineal: mezclar
   varias escenas a la vez hace que se pierda el hilo. Con el libreto partido por escenas, esto
   es literalmente un fichero.
3. Cuando se cierre una escena, actualiza su estado en la escaleta **y** su fecha en
   `README.md`.
4. Escribe en el fichero que corresponda, no en uno nuevo. Si un dato no tiene sitio, casi
   siempre es porque falta decidir algo: eso es una pregunta, no un fichero extra.
5. Al final de la sesión, deja escrito lo que has decidido y lo que queda abierto. La
   siguiente sesión no tiene tu contexto.

## Convenciones

- Ficheros y carpetas en minúsculas, sin tildes, con guiones: `sonido.md`, `escaleta.md`.
- Las escenas se numeran con dos dígitos: `1.`, `2.`, `10.`.
- Los ficheros del libreto se llaman `NN-nombre.md`, con el número de escena delante:
  `05-el-tiro-al-blanco.md`. El número no se reutiliza ni se renumera.
- Las acotaciones van entre paréntesis: `(el pato gira la cabeza hacia el público)`.
- Los cambios de sonido se marcan con `>>` y los de luz con `**`: `>> un alaseteo`. Los
  efectos llevan su número de cue y la música su número de pista:
  `>> [S-07] un alaseteo`, `>> ♪ «Vuela» (p. 06)`.
- Las preguntas abiertas se dejan como `TODO:` al final del fichero, no interrumpen el texto.

## Un fichero por escena

**El libreto son doce ficheros, uno por escena, no uno con doce escenas dentro.** Decidido por
el autor (2026-09-27). El motivo es que la unidad de trabajo del proyecto ya es la escena: una
sesión trabaja una escena, y con el libreto partido eso es literalmente un fichero.

**Lo que NO se parte:**

- **`guion/sinopsis.md`** y **`guion/escaleta.md`** se leen enteros y se quedan como están. La
  sinopsis es la brújula y la escaleta es el índice; las dos pierden su función en cuanto se
  parten. Los actos tampoco se hacen ficheros: viven en la tabla de actos de la escaleta.

**Cada fichero de escena tiene la misma estructura:**

```
# NN. Título

> Estado, acto, música          ← la cabecera, siempre igual

## Qué ocurre                   ← el hecho, sin adornos
## Por qué está aquí            ← la función en el viaje
## Se repite en                 ← los elementos que vuelven
## Texto                        ← aquí va el libreto
## TODO(preguntar)              ← al final, no interrumpiendo
```

Con esto, leer un acto entero seguido es un `cat`:

```bash
cat guion/libreto/0[5-8]-*.md
```

## El sonido

Todo el sonido de la obra se decide en Ableton Live y se anota en `recursos/sonido.md`. El
disco, los efectos y la parte técnica son un solo asunto: hay un Set, hay un operador, hay un
solo fichero.

### Tres niveles, tres sitios

**El libreto dice el sonido. `sonido.md` dice la máquina.** Esta es la regla que lo deja claro:

| | Qué lleva | Qué no lleva |
|---|---|---|
| `guion/libreto/NN-*.md` | Lo que se oye, en términos dramático-teatrales. Cómo suena de verdad, con su cue. | Nombres de dispositivo, de pista de Live, de efecto, de automation, dB. |
| `recursos/sonido.md` | La implementación en Live: arquitectura del Set, tabla de cues, por qué cada sonido suena así. | Acotaciones de manipulación, indicaciones de luz, texto de la obra. |
| `AGENTS.md` | Esta convención. | Nada del sonido concreto. |

Consecuencia práctica: si aparece un `Resample` en el libreto, está mal; si aparece
«el ventilador hace un ruido espantoso» en `sonido.md`, está mal. Cada cosa en su sitio.

### Las cues

- **Un cue es un sonido con nombre.** Tiene un identificador corto y estable que se puede
  escribir en el libreto y buscar con `grep`.
- **Dos series, porque son dos cosas distintas:**
  - `P-nn` — las nueve pistas del disco, con su número de pista del disco (`P-02` es
    «Avivas el fuego», la 2 del disco). Es el mismo número que usan `guion/escaleta.md` y
    `investigacion/referencias.md`, así que no hay que traducir.
  - `S-nn` — los efectos sonoros, numerados en el orden en que salen en la obra, de la escena
    01 a la 11.
- **La numeración es sagrada.** Un número de cue no se reutiliza, no se renumera y no se
  reasigna. Si un efecto se cae, se marca `caído` y su número queda libre para siempre: quien
  tenía memorizado `S-07` en la gira anterior tiene que encontrar ahí lo mismo, o nada.
- **El mismo efecto puede sonar en varias escenas con cues distintas** (`S-01` y `S-14` pueden
  ser el mismo latido, uno de la escena 01 y otro de la de la 11 con otro tratamiento). Lo que
  se repite es el sonido; el cue es una ocurrencia concreta.

### No se inventa el sonido

La misma regla que las letras y que los datos de la banda, aplicada a los efectos:

- Si un sonido no está en la sinopsis, en el autor o en `sonido.md`, se marca
  `TODO(preguntar):` y no se describe inventando. **Un efecto inventado en un libreto se
  representa mañana y no funciona pasado mañana.**
- Se puede describir dramáticamente un efecto que se sabe que va a existir aunque no esté
  resuelto técnicamente: eso no es inventar el sonido, es decidir el efecto. Lo que no se hace
  es inventar cómo se hace.
- Si el efecto usa un fragmento de una canción, es un fragmento y se cita, no se vuelca.

### Cómo se dispara

**Un Launch por cue, todo a mano** (decidido por el autor, 2026-09-27). Lo dispara quien
opera, siguiendo a la manipulación, no siguiendo un reloj. Las consecuencias asumidas:

- **El disco también es manual.** No hay una Launch por escena con la música automatizada: cada
  pista del disco es su propio cue `P-nn`, y el operador lo lanza. El disco no deja de sonar
  porque el títere se retrase, pero tampoco le sigue el paso solo.
- **Cada cue necesita poder callarse.** Un efecto que no tiene forma de parar es un efecto que
  se va alPause accidental. Cada cue lleva su forma de parada en `sonido.md` (choke group,
  Launch Mode, corte manual) y el operador la tiene que tener a mano.
- **Los cues del disco duran lo que dura la pista.** Si una escena usa «Está bien» entera, el
  cue dura 3:17. Para cortar antes hace falta un segundo cue. `TODO(preguntar):` si hay alguna
  escena donde la música tenga que entrar o salir dentro de la pista.
- **Nada de esto se decide aún en el Set.** La arquitectura concreta (pistas, buses, Launch
  Modes, choke groups, key mapping) está en `recursos/sonido.md` y se escribe cuando empiece
  el trabajo de sonido.
