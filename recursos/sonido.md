# Sonido

> **Todo el sonido de la obra, en Ableton Live.** La música del disco, los efectos sonoros y
> la parte técnica. Un solo fichero porque hay un solo Set, un solo operador y un solo
> interruptor.
>
> **Estado: convención decidida (2026-09-27). Set sin construir.** Está escrita la forma de
> trabajar —qué es un cue, cómo se numera, cómo se dispara— y está inventariados los sonidos
> que la sinopsis ya nombra. No hay una sola pista de Live construida todavía.
>
> La convención de marcado vive en `AGENTS.md`, sección «El sonido». Este fichero es su
> ejecución: la tabla de cues y las decisiones técnicas.

## Los tres niveles

| | Qué lleva | Qué no lleva |
|---|---|---|
| `guion/libreto/NN-*.md` | Lo que se oye, en términos dramático-teatrales, con su cue. | Nombres de dispositivo, de pista, de efecto, dB. |
| `recursos/sonido.md` | La implementación en Live y por qué suena así. | Acotaciones de manipulación, indicaciones de luz, texto de la obra. |
| `AGENTS.md` | La convención. | Nada del sonido concreto. |

## El Set

**Un Set, un operador, un Launch por cue.** Decidido por el autor (2026-09-27).

> **Ableton Live 12.** Confirmado por el autor (2026-09-27). Importa porque los nombres de
> los dispositivos han cambiado entre versiones, y lo que se escriba aquí tiene que existir en
> la versión con la que se va a construir.
>
> `TODO(preguntar):` con qué superficie de control se opera en escena (teclado, Push, otra).
> Cambia el key mapping entero.

### Cómo se dispara

Cada cue es una escena de Launch en Session View, y lo lanza quien opera siguiendo la
manipulación, no siguiendo un reloj. Consecuencias asumidas:

- **El disco es manual también.** No hay una Launch por escena de la obra con la música
  automatizada: cada pista del disco es su propio cue `P-nn` y el operador lo lanza. Si el
  títere se retrasa, la pista no se para sola.
- **Cada cue tiene que poder callarse.** Un efecto sin forma de parar se acaba en el Pause
  accidental, y en un escenario hay que hacerlo sin mirar la pantalla. Cada cue lleva su forma
  de parada escrita en su fila: *choke group*, *Launch Mode: Gate/Toggle*, corte manual, o lo
  que toque.
- **Los cues del disco duran lo que dura la pista.** «Está bien» son 3:17. Si una escena
  necesita menos, hace falta un segundo cue con un corte antes.

### Cómo se llama cada pista

El nombre de la pista en Live es el nombre del cue, y nada más:

```
latido-01            audio       → [S-01]
relampagos-10         audio       → [S-19]
caja-vacio            audio       → [S-15]
p-02-avivas-el-fuego  audio       → [P-02]
```

Razón: quien está a oscuras delante de Ableton ve una rejilla de nombres y tiene que encontrar
la suya en menos de un segundo. El cue va en el nombre, no memorizado.

### Pistas, buses y master

**Sin decidir.** `TODO(preguntar):` cuántas pistas de audio, cuántas de MIDI (si la banda
tocando en escena necesita que Live lo escuche), si hay retornos de reverb y delay compartidos
o uno por efecto, y qué hay en el master. Se escribe cuando se empiece a construir el Set, no
antes: decidir la arquitectura sin material delante es inventarla.

Lo que sí está dicho:

- **Un canal de Effects y otro de Returns por defecto** hasta que se demuestre que no vale.
- **El bus de la banda en vivo es cosa de `recursos/escena.md`**, no de aquí: si la banda toca
  en directo y se necesita que pase por Live, es otra cadena y otra decisión.

## La tabla de cues

Una fila por cue. Las columnas que se rellenan a medida que se construya el Set.

| Cue | Escena | Qué se oye | Fuente del sonido | Cómo en Live | Disparo | Parada |
|---|---|---|---|---|---|---|
| S-01 | 01 | el latido, con la sala debajo, y el aire que se abre encima hasta que la pista está entera | **el bombo de «Avivas el fuego»** (decidido por el autor, 2026-09-27) + sala | «El latido», abajo | — | — |
| S-02 | 04 | el bucle de VHS que devuelve el tramo hacia atrás | imagen + audio de la propia escena | — | — | — |
| S-03 | 07 | el sonido de «salir por donde entraron» (cisterna, según la sinopsis) | `TODO(preguntar):` | — | — | — |
| S-04 | 08 | el ventilador que no deja avanzar la furgoneta | `TODO(preguntar):` ¿ventilador real grabado? | — | — | — |
| S-05 | 08 | la furgoneta chocando contra el ojo de la luna | silencio, más la vídeo de Méliès | — | — | — |
| S-06 | 09 | barras de colores de señal con su pitido | el pitido es del sistema de telecolor, no de la banda | — | — | — |
| S-07 | 10 | relámpagos y truenos, sin que llueva | `TODO(preguntar):` | — | — | — |
| S-08 | 11 | el latido vuelve, y la pista está entera desde el primer segundo: el mundo florece | **la misma pista que S-01** | «El latido», abajo | — | — |

Y los cues del disco, que no se inventan: son las nueve pistas, con su número de pista.

| Cue | Escena | Pista | # | Duración |
|---|---|---|---|---|
| P-02 | 01 | «Avivas el fuego» | 02 | 6:41 |
| P-05 | 02 | «Está bien» | 05 | 3:17 |
| P-08 | 07 | «La puerta» | 08 | 4:43 |
| P-01 | 08 | «Ser artista» | 01 | 3:58 |
| P-06 | 09 | «Vuela» | 06 | 3:33 |
| P-09 | 10 | «Seica» | 09 | 4:55 |
| P-02 | 11 | «Avivas el fuego», otra vez | 02 | 6:41 |
| P-05 | 11 | «Está bien», otra vez | 05 | 3:17 |
| P-07 | 04 | «Lo llaman vida» | 07 | 3:49 |

Pistas y duraciones: `investigacion/referencias.md`. Qué pasa en las escenas 03, 05 y 06 está
sin decidir (`TODO(preguntar):` en `guion/escaleta.md`).

## El latido — escenas 01 y 11

El primer sound design de la obra, y el que fija el patrón de todos los demás.

### Lo que se decidió

- **El material es el bombo de «Avivas el fuego»** (p. 02), no una grabación de corazón
  (decidido por el autor, 2026-09-27). Consecuencias: el latido no necesita grabarse, y ya va
  al tempo de la pista que suena en la escena.
- **Con la sala debajo.** El latido no suena solo: hay una capa de ruido de sala debajo desde
  el principio, para que el corazón no esté solo en el mundo (decidido por el autor,
  2026-09-27).

> **En revisión.** El autor ha pedido un latido sintetizado en MIDI a un modelo que controla
> Live por MCP, con carácter de estetoscopio y resonancia de caverna, para verlo y oírlo antes
> de decidir. Si ese latido sustituye al bombo, cambia lo de abajo: se pierde la sincronía
> automática con la pista (ver `TODO` del tempo) y el cue `S-01` pasa a ser un instrumento, no
> un filtro. Decisión pendiente.

### Lo que se deduce de esas dos decisiones

**El latido no es un efecto: es la pista, con todo tapado menos el bombo.** Si el material es
el bombo de «Avivas el fuego» y esa misma pista suena en la escena 01, entonces el latido y la
canción son el mismo audio en el mismo momento. La escena 01 no tiene un cue de efecto y otro
de música: **tiene un solo playback que se abre.**

```
  ESCENA 01                                        ESCENA 11
  ─────────                                        ─────────
  P-02 «Avivas el fuego», 0:00                    P-02 «Avivas el fuego», 0:00
  audio ─┬─ Auto Filter (cerrado)  ← el latido     audio ────── sin filtro
         └─ Volume        (casi cero)   ┐                    la pista entera
  fondo: sala ────────────────────────┘                    desde el segundo uno
         │                                                   │
   sala → latido → canción                           el latido sigue debajo
```

**La salida del latido a la pista completa es un cue de verdad, no una metaphor.** En la
escena 11, «el mundo florece» es la misma operación con el filtro ya abierto: la misma
apertura, ejecutada en el otro sentido. El público oye el mismo sonido dos veces y no lo
reconoce conscientemente, pero nota que la segunda vez todo llega ya.

**Esto arregla de paso el problema de los graves.** Un latido grabado en contacto vive entre
40 y 60 Hz y en un teatro no se oye. El bombo de una pista real tiene armónicos, y aunque se
filtre a una banda media se le queda el cuerpo. `TODO(preguntar):` sigue haciendo falta saber
con qué PA se representa, pero el riesgo es mucho menor que con un sample de pecho.

### Propuestas que salen de aquí (no son decisiones)

> Lo que sigue sale de las dos decisiones anteriores, pero **el autor no lo ha decidido**.
> Está aquí para que se pueda rechazar.

- **El fondo de sala como capa continua de toda la obra**, no como un cue. Arranca con el
  espectáculo y se apaga al final, y no tiene número de cue porque no se dispara: está siempre
  debajo. Como efecto colateral resuelve la pregunta de si hay algún momento de silencio real
  en la obra (`TODO` más abajo): con la sala debajo, no lo hay.
- **Una sola pista de audio, no dos.** Dos pistas con el mismo archivo empezarían desfasadas
  en cuanto el operador lance la segunda. Una sola reproducción y un filtro es lo único que no
  puede desfasarse.
- **La apertura con un knob, no con un cue.** Con un Launch por cue, una apertura de filtro es
  más un control continuo que un disparo. La alternativa, si se quiere discreto: una clip de
  MIDI con la automatización grabada que se lanza, que obliga a armar grabación y en un AVE es
  frágil. `TODO(preguntar):` ¿a mano con mando, o con la automatización?

## El flujo de trabajo del canal

Cuando se describa un efecto en este canal, la salida va a la tabla de arriba. El orden es:

1. **Qué se oye** — una frase dramática, la que irá al libreto. Se decide antes de nada: si no
   se puede decir en una frase, todavía no se sabe qué efecto es.
2. **De dónde sale el material** — una grabación real, un sample de campo, un sintetizador, o
   un fragmento del disco. Si no está resuelto: `TODO(preguntar):`.
3. **Cómo se hace en Live** — pista, efecto, automatización, Launch Mode. Esto se escribe con
   Ableton delante, no de memoria.

Los pasos 1 y 3 son de este canal. El 2 necesita material.

## TODO(preguntar)

- **El tempo de «Avivas el fuego» y en qué segundo entra el primer bombo.** Es lo que
  bloquea la construcción del latido (escenas 01 y 11, «El latido» más arriba). No está en
  `investigacion/referencias.md`. **120 es un valor de trabajo, no el tempo de la obra.**
- **De dónde sale el ruido de sala**, y **qué se oye debajo de la sala**: ruido de sala de
  verdad (una calle, un hangar, un sitio reconocible) o solo aire. De eso depende si la escena
  01 tiene sitio o tiene mundo. En Live sería un clip en bucle con loop fade largo, para que el
  empalme no se oiga.
- **La pista de fondo de sala.** Material, nivel, y si cruza toda la obra o solo la escena 01.
  Depende de si el PA es de la sala o de la compañía.
- **Graves en la sala.** Un latido de pista real tiene más cuerpo que uno grabado en
  contacto, pero sigue habiendo que saber con qué PA se representa.
  `TODO(preguntar):` con qué PA y con qué caja.
- **El Set no existe todavía.** Pistas, buses, retorno, master, key mapping: sin decidir. La
  columna «Cómo en Live» de la tabla está vacía a propósito.
- **Qué material hay grabado.** No hay inventario de grabaciones. ¿Qué sounds, qué field
  recordings, qué hay en el móvil de alguien?
- **La música dentro de la pista.** ¿Alguna escena necesita que la música entre o salga *dentro*
  de una pista? Sería un segundo cue con corte, y por ahora no lo hay (`AGENTS.md`, «Cómo se
  dispara»).
- **El eco.** Si la sala tiene reverberación y la música del disco va amplificada, ¿el disco
  entra por el PA directamente o pasa por Live? Afecta a toda la arquitectura.
- **Escenas 03, 05 y 06.** Sin decidir en la escaleta, no tienen cues.
- **Silencio real.** ¿Hay algún momento de obra en el que no suena nada del todo? Es el cue
  más difícil de disparar a mano.
