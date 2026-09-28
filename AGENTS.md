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
│       ├── 01-el-corazon.md
│       ├── 02-ninos-proyectados.md
│       ├── 03-el-sombrerero.md
│       ├── 04-la-furgoneta.md
│       ├── 05-el-tiro-al-blanco.md
│       ├── 06-la-reina.md
│       ├── 07-la-salida-que-no-esta.md
│       ├── 08-la-nina-triste-y-el-ventilador.md
│       ├── 09-la-senal.md
│       ├── 10-lo-ancestral.md
│       ├── 11-el-fuego.md
│       └── 12-cuerda-floja.md
├── recursos/
│   ├── audiovideo.md              todo el sonido y el vídeo de la obra, desde Ableton Live
│   ├── fichas.md                  personajes, objetos y títeres uno a uno
│   ├── escena.md                  puesta en escena, manipulación, técnica
│   └── produccion.md              calendario, presupuesto, derechos
└── investigacion/
    └── referencias.md             datos verificados sobre banda y disco, con fuente
```

`.opencode/` no aparece en el árbol porque no es material de la obra: es configuración de
opencode (los sub-agentes, sus permisos). Va de **Datos**, como el resto de la estructura.

```
.opencode/
├── agents/          sub-agentes: contexto y permisos propios
│   └── git.md
└── skills/          skills: procedimientos que se cargan en tu contexto
    └── cerrar-escena/SKILL.md
```

## Para qué sirve cada fichero

- **`guion/sinopsis.md`** — el norte. Si una escena nueva no encaja con la sinopsis, o
  cambia la sinopsis, se actualiza aquí primero.
- **`guion/escaleta.md`** — el índice y el estado de avance. Una línea por escena, con su
  estado. Es lo primero que se lee y lo primero que se actualiza. Una escena pasa por:
  `idea` → `boceto` → `revisada` → `cerrada`.
- **`guion/libreto/`** — el texto en sí, con las acotaciones, **un fichero por escena**
  (`NN-nombre.md`, dos dígitos, minúsculas, guiones). El texto se escribe **antes** de que la
  escena esté `revisada`: es lo que la hace pasar por `idea` y `boceto`. `revisada` quiere decir
  que el texto está y ya no se toca. Ver «El protocolo: `revisada` es la puerta».
- **`recursos/audiovideo.md`** — todo el sonido y el vídeo de la obra. La música del disco (qué
  pista en qué momento y por qué suena ahí), **los efectos sonoros** y **las proyecciones de
  vídeo**, con la descripción de cómo se hacen en Ableton Live. Ver «El sonido y el vídeo» más
  abajo.
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
3. Cuando se cierre una escena, actualiza su estado en la escaleta **y** la fecha en el
   bloque `## Estado` de la misma escaleta. Ver «`cerrar-escena`: cerrar una escena» y el
   paso 1 de las herramientas.
4. Escribe en el fichero que corresponda, no en uno nuevo. Si un dato no tiene sitio, casi
   siempre es porque falta decidir algo: eso es una pregunta, no un fichero extra.
5. Al final de la sesión, deja escrito lo que has decidido y lo que queda abierto. La
   siguiente sesión no tiene tu contexto.

## Git

**Varias sesiones de kimaki comparten este mismo directorio.** Cada una tiene su hilo, pero
todas escriben en el mismo árbol de trabajo. Por eso las reglas de git aquí no son las de un
proyecto normal: son las de un proyecto con otro agent al lado.

### Un commit es una confirmación de cambios

**El commit no es una unidad de trabajo: es un punto de control.** Confirma que algo ha cambiado
y lo deja escrito. No es la escena, ni el acto, ni el fichero. Se hace **normalmente cuando una
escena pasa a `revisada`** en la escaleta, porque es el momento en que hay algo que confirmar.
También se hace cuando se corrige algo, cuando se toma una decisión que no es de una escena, o
cuando el autor lo pide. **No hace falta esperar a tener la escena entera para no perder el
trabajo.**

### Nunca `git add -A`

- **En un árbol compartido, `-A` se lleva puesto también lo que otra sesión tiene a medio
  escribir.** Se commitea fichero a fichero:
  `git add guion/libreto/12-cuerda-floja.md guion/escaleta.md`.
- **Antes de commitear, `git status`.** Si hay cambios que no son tuyos, **no los commitees**.
  Dímelos y pregunta. Subir el trabajo a medio hacer de otra sesión no es un favor: es meter en
  la historia algo que el autor no ha visto.
- **Para saber de quién es un cambio:**
  ```bash
  kimaki session editors guion/sinopsis.md
  ```
  Sale la sesión que lo escribió por última vez y hace cuánto. Si no es la tuya, es de otra.

### El mensaje

- **Nombra lo que ha cambiado, no la unidad de trabajo.** `libreto 12: la cuerda floja a
  revisada`, `escaleta: la 12 entra en el acto III`, no `avances`.
- Si el commit no coincide con una escena cerrada, **el mensaje dice en qué estado estaba**.
- Un commit puede no tener nada que ver con una escena: una corrección, un dato, una decisión de
  estructura. Eso es normal y está bien.

### Nunca hay push sin pedirlo

- El **push** solo cuando el autor lo pida.
- Antes de push, decir qué va y en qué commit. Si hay cambios sin commitear de otra sesión,
  se mencionan y se dejan fuera.

### Quién escribe qué

**Hay tres sesiones, y cada una tiene sus ficheros.** Decidido por el autor (2026-09-28). Un
fichero tiene un dueño: si necesitas tocar uno que no es tuyo, **se lo dices al autor y lo
dices aquí**, pero no lo escribes.

| Sesión | Escribe | No toca |
|---|---|---|
| **Guion** | `guion/sinopsis.md`, `guion/escaleta.md`, todo `guion/libreto/` | `recursos/`, `investigacion/` |
| **Ableton** | `recursos/audiovideo.md` — disco, efectos, cues, el Set de Live, la red de TouchDesigner | `guion/`, `investigacion/`, `AGENTS.md` |
| **Datos** | `investigacion/referencias.md`, `recursos/fichas.md`, `AGENTS.md`, la estructura del proyecto (`README.md`) y la configuración de opencode (`.opencode/`) | `guion/`, `recursos/audiovideo.md` |

Lo que **no** está repartido y sigue sin dueño: `recursos/escena.md` (puesta en escena) y
`recursos/produccion.md` (calendario, presupuesto, derechos). Hasta que se decida, son de quien
los escriba, avisando antes.

- **El reparto no es una suggestion, es la razón de poder ir en paralelo.** Las tres sesiones
  pueden trabajar a la vez **porque no comparten ficheros**. En cuanto dos tocan el mismo, una
  pisa a la otra y ninguna sabe qué se ha perdido: por eso la tabla es de un solo dueño.

### Cómo se le habla a otra sesión

Cada sesión tiene su hilo de Discord. Para pasarle algo a la que le toca, se le manda un
mensaje a su hilo con `kimaki send --thread`:

| Sesión | Hilo |
|---|---|
| **Guion** | `1553690300218605640` |
| **Ableton** | `1553736444798042246` |
| **Datos** | `1553709651860656131` |

```bash
kimaki send --thread 1553736444798042246 --prompt 'La escena 08 necesita un efecto nuevo: ...'
```

**Un commit no es un mensaje.** Si algo es de otra sesión, se le manda a su hilo y se sigue. La
otra sesión lo mete en su fichero; quien escribe el fichero es quien commitea.

**Dos mensajes por sesión, y luego a callar.** Decidido por el autor (2026-09-28). En un diálogo
entre sesiones, cada una tiene **dos mensajes**. Al segundo, la conversación se para: lo que quede
sin resolver se le pregunta al autor aquí, y no se sigue encadenando.

El motivo es concreto: las sesiones se Contestan entre sí, y sin tope una observación pequeña
genera otra, y la siguiente, y ninguna se para. Con dos, la primera observación se aplica y la
segunda avisa. Lo que haga falta de más, se le pregunta a la persona.

### Los efectos y la música se deciden en Ableton

**Si al escribir una escena sale un sonido —un efecto, un corte, una música, un silencio que
significa algo, un momento de la pista— eso no se resuelve ahí.** Se propone y se manda a
Ableton.

- La sesión de Guion **nombra** el sonido dramáticamente, como lo oye el público: `>> un
  alaseteo`, `>> ♪ «Vuela» (p. 06)`. Eso se hace siempre, desde el primer día, y no se espera a
  nada. **Nombrar el sonido no es encargarlo.**
- Ableton es la que decide **cómo suena** y lo anota en `recursos/audiovideo.md` con su número de
  cue.

Igual con la otra dirección: si a Ableton le falta saber qué hace una escena para poder decidir
un sonido, se lo pregunta al hilo de Guion en vez de adivinarlo. Lo mismo con **Datos**: si
falta un dato de la banda o del disco, se pregunta ahí en vez de suponerlo.

### El protocolo: `revisada` es la puerta

**Hasta que una escena no está en `revisada` en la escaleta, no se le pasa nada a Ableton.** Ni
los efectos, ni los sonidos, ni las pistas. Decidido por el autor (2026-09-28).

El estado está en `guion/escaleta.md`, y es la única fuente de la verdad:

```bash
grep '| 12 |' guion/escaleta.md     # la fila dice el estado
```

| Estado de la escena | Qué hace Guion | Qué hace Ableton |
|---|---|---|
| `idea` | Escribe el texto. Nombra los sonidos en el libreto. **No manda nada.** | No sabe que existe |
| `boceto` | Lo mismo. Acaba el texto y lo relee. **No manda nada.** | No sabe que existe |
| `revisada` | Actualiza el estado en la escaleta y **manda la lista de sonidos** | Los construye y asigna cues |
| `cerrada` | Nada pendiente | Idem, si hace falta corregir algo |

**Por qué la puerta:** una escena en `boceto` todavía cambia. Un efecto construido sobre un
texto que se va a reescribir es un efecto que hay que tirar y volver a hacer, con su cue gastado
— y la numeración de cues es sagrada, así que ese número queda libre para siempre. La puerta
protege a Ableton de un churn que no puede deshacer.

**El mensaje a Ableton lleva cinco cosas**, y si le falta una, no se puede empezar:

1. **Qué escena y en qué estado.** «Escena 12, `revisada` esta tarde».
2. **Qué necesita.** El efecto o la pista, con su nombre tal como lo escribió Guion.
3. **Dónde y cuándo.** En qué punto de la escena, y en qué momento.
4. **Por qué en ese momento.** Qué le pasa a la escena, a la imagen o al público justo ahí.
5. **De dónde sale el material.** Si es un archivo, una pista del disco, una grabación que hay que
   conseguir, o algo que hay que fabricar. **Si la respuesta es «todavía no lo sé», el material
   no está resuelto** y la puerta no se puede dar por buena: eso se pregunta antes, aquí, en
   `investigacion/referencias.md` o en el hilo de Guion.

**Ableton comprueba la puerta antes de empezar.** Si llega una propuesta de una escena que no
está en `revisada`, lo dice y no la trabaja: no es suyo decidir que un texto ya está. Y si le
falta algo para construir el efecto, pregunta a Guion; no lo deduce.

### El numerito de cues lo fija la puerta

Los `S-nn` se numeran **en el orden en que las escenas llegan a `revisada`**, no en el orden en
que Guion las escribe. Como el estado de cada escena está en la escaleta, la numeración se
deduce de ahí.

Esto tiene una consecuencia que conviene decir en voz alta: si la 12 se revisa antes que la 05,
**la 12 se lleva los cues bajos y la 05 los altos**, aunque en la obra la 05 suene antes. No es
un error: es que el número identifica un sonido, no su posición en la obra. Lo que no puede
pasar es que un número se reutilice, se renumere o se reasigne. Una escena que vuelve a `boceto`
no mueve los cues que ya tenía: si el efecto cambia, el viejo se marca `caído` y el nuevo
coge el siguiente número libre.

- **Antes de escribir un fichero, mira quién lo escribió por última vez:**
  ```bash
  kimaki session editors guion/escaleta.md
  ```
  Si fue hace poco, esa sesión sigue trabajando en él. Se espera.
- La escena N depende del estado que dejó la N-1, así que dentro de `guion/` **una escena por
  sesión**. Eso no contradice el reparto: es lo que pasa por dentro de la sesión Guion.
- El worktree (`kimaki send --worktree escena-12`) queda como recurso de emergencia, no como
  forma normal de trabajar: `escaleta.md` y `sinopsis.md` dan conflicto siempre y hay que
  fusionar a mano.

## Las herramientas

En `.opencode/` hay un sub-agente y un skill. **No son dos maneras de hacer lo mismo, y no se
sustituyen uno por otro.** La diferencia es de permisos, y por eso hay dos cosas en vez de
una:

| | Qué es | Cuándo se usa |
|---|---|---|
| **Sub-agente `@git`** | Otro agente, con contexto y permisos propios | Para commitear, revisar el árbol o tocar GitHub |
| **Skill `cerrar-escena`** | Un checklist que se carga en **tu** contexto | Cuando una escena llega a `revisada` |

Un skill es documentación: se carga en la sesión que lo invoca, y esa sesión conserva todos
sus permisos. Leído, «no hagas push sin permiso» sigue siendo un consejo. El sub-agente no
recibe el consejo: tiene el push en `ask` y no puede escribir ficheros. **En un árbol con
tres sesiones, un consejo y una valla no valen lo mismo.**

### `@git`: el control de versiones

Se invoca con `@git`, o por su cuenta cuando toca commitear. **La sección de git de arriba
son las reglas; él es quien las aplica.** No las repito aquí.

Lo que `@git` añade sobre esas reglas:

- **Los permisos de verdad, no el prompt.** `edit: deny` — no puede escribir un solo fichero
  de la obra, así que no puede reescribir la obra yllamándola «un retoque». `git commit` y
  `git push` en `ask`. Y en `deny`: `git add -A`, `git add .`, `git checkout` (salvo `-b`),
  `gh api`. Lo que no puede hacer, no lo intenta.
- **Nunca commitea por su cuenta.** Stagea fichero a fichero, redacta el mensaje, enseña
  `git diff --cached` y **para a preguntar**. Si un cambio no es suyo, no lo commitea: lo
  reporta. Aunque el mensaje sea de otra sesión.
- **GitHub, con `gh`.** Lectura siempre (`gh pr status`, `gh issue list`, `gh pr diff`…);
  escritura en `ask`: PR e issues. Ver abajo, que el flujo tiene un raíl.

**El raíl de las ramas.** La rama es del **árbol de trabajo**, no de la sesión: las tres
sesiones comparten el directorio, así que si `@git` se mueve a una rama, **Guion y Ableton se
mueven con él**, con sus cambios sin commitear encima y sus commits cayendo en su rama. Por
eso no cambia de rama por su cuenta, solo con el árbol limpio salvo lo suyo, y vuelve a
donde estaba. **Si hay trabajo de otra sesión sin commitear, no hay flujo de PR posible:**
es un worktree, o se commitea en `main` y ya.

**PR.** El flujo por defecto **sigue siendo commit local en `main` y sin push**. Un PR se abre
solo si lo pides, y no se mergea porque exista: se mergea cuando lo dices.

**Issues para los `TODO(preguntar)`.** Los pendientes de los libretos se pierden, porque la
siguiente sesión no tiene contexto. `@git` puede convertirlos en issues, **pero solo si se
lo pides**: deduplica contra los que ya hay, te propone lista y títulos antes de crear nada,
y **no cierra ninguno por su cuenta** — el `TODO` lo borra quien escribió el fichero, que
es su sesión.

### `cerrar-escena`: cerrar una escena

Se carga sola cuando toca llevar una escena hasta `revisada`. Es un checklist, no un
delegado: **el texto lo escribes tú**, la skill es el orden en que se hace todo lo demás.

Lo que hace bien y donde se falla siempre a mano: **el estado de una escena vive en tres
sitios a la vez**, y basta con olvidar uno.

| Dónde | Qué se toca |
|---|---|
| `guion/libreto/NN-nombre.md` | La cabecera: `> **Estado:**` |
| `guion/escaleta.md` | La fila de la escena, columna **Estado** |
| `guion/escaleta.md` | El bloque `## Estado` del final, que resume los recuentos |

El tercero es el que se lee primero y **es el que se miente solo**: sigue diciendo «Sin
escenas `revisada`» después de que la haya. Escribe el texto *antes* de `revisada`; lo que
marca el avance a `idea` y `boceto` es precisamente eso.

**Ojo: `README.md` no existe.** Este documento y el flujo de trabajo lo daban por hecho, pero
nunca se creó — no sale ni en la historia de git. Por eso el paso 3 del flujo va a la fecha
en el `## Estado` de la escaleta. **Nadie lo crea por su cuenta:** es una decisión del autor,
y el fichero sería de **Datos**.

## Convenciones

- Ficheros y carpetas en minúsculas, sin tildes, con guiones: `audiovideo.md`, `escaleta.md`.
- Las escenas se numeran con dos dígitos: `1.`, `2.`, `10.`.
- Los ficheros del libreto se llaman `NN-nombre.md`, con el número de escena delante:
  `05-el-tiro-al-blanco.md`. El número no se reutiliza ni se renumera.
- Las acotaciones van entre paréntesis: `(el pato gira la cabeza hacia el público)`.
- Los cambios de sonido se marcan con `>>` y los de luz con `**`: `>> un alaseteo`. La música
  lleva su número de pista, que es fijo y sí se escribe: `>> ♪ «Vuela» (p. 06)`.
  **Los efectos no llevan número en el libreto.** El `>>` va con el nombre del sonido tal como lo
  oye el público; el `S-nn` se asigna al pasar la escena a `revisada` y vive solo en
  `recursos/audiovideo.md`. Ver «Las cues».
- **El vídeo también va con `>>` y también sin número**, por la misma razón: `>> un vídeo de niños
  proyectados`. El `V-nn` se asigna en la puerta, igual que el `S-nn`.
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

## El sonido y el vídeo

Todo el sonido y el vídeo de la obra se deciden en Ableton Live y se anotan en
`recursos/audiovideo.md`. El disco, los efectos, las proyecciones y la parte técnica son un solo
asunto: hay un Set, hay un operador, hay un solo fichero.

### Tres niveles, tres sitios

**El libreto dice el sonido y el vídeo. `audiovideo.md` dice la máquina.** Esta es la regla que lo
deja claro:

| | Qué lleva | Qué no lleva |
|---|---|---|
| `guion/libreto/NN-*.md` | Lo que se oye y lo que se ve, en términos dramático-teatrales. Cómo suena y cómo se ve de verdad, con su cue. | Nombres de dispositivo, de pista de Live, de efecto, de automation, dB, nombres de nodo de TouchDesigner. |
| `recursos/audiovideo.md` | La implementación: arquitectura del Set, tabla de cues, por qué cada sonido suena así, cómo se lanza cada vídeo. | Acotaciones de manipulación, indicaciones de luz, texto de la obra. |
| `AGENTS.md` | Esta convención. | Nada del sonido ni del vídeo concretos. |

Consecuencia práctica: si aparece un `Resample` en el libreto, está mal; si aparece
«el ventilador hace un ruido espantoso» en `audiovideo.md`, está mal. Cada cosa en su sitio.

### Las cues

- **Un cue es una cosa que hay que lanzar con nombre.** Tiene un identificador corto y estable
  para poder buscarlo. **Los números de cue solo existen en `recursos/audiovideo.md`.** No se
  escriben en el libreto: los asigna Ableton al pasar la escena a `revisada`, y desde ese momento
  viven en un solo sitio y no pueden desincronizarse. En el libreto va el nombre tal como lo ve
  o lo oye el público.
- **Tres series, porque son tres cosas distintas:**
  - `P-nn` — las nueve pistas del disco, con su número de pista del disco (`P-02` es
    «Avivas el fuego», la 2 del disco). Es el mismo número que usan `guion/escaleta.md` y
    `investigacion/referencias.md`, así que no hay que traducir. **Este sí va en el libreto**,
    porque es fijo y está desde el primer día: `>> ♪ «Vuela» (p. 06)`.
  - `S-nn` — los efectos sonoros, numerados **en el orden en que las escenas llegan a
    `revisada`**. Ver «El numerito de cues lo fija la puerta»: el número identifica un sonido,
    no su posición en la obra.
  - `V-nn` — las proyecciones de vídeo, **numerados igual que los `S-nn` y por la misma puerta**.
    El vídeo es material tan suena como un efecto: lo dispara el operador desde el mismo sitio y
    en el mismo momento, y se decide al pasar la puerta, no desde el primer día. Así que no
    necesita reglas propias, y no se le inventa una serie nueva: solo otra columna.
- **El vídeo va en el mismo fichero que el sonido.** Decidido por el autor (2026-09-28): el
  fichero se llama `recursos/audiovideo.md` y cubre los dos. **No se crea `recursos/video.md`.**
  El motivo es que hay un solo operador disparando desde un sola mesa: partir la lista en dos
  se nota justo en el momento en que hay que clavar un vídeo y un sonido a la vez. Si
  TouchDesigner crece y pide su propio fichero, se parte entonces, que es barato.
- **La numeración es sagrada.** Un número de cue no se reutiliza, no se renumera y no se
  reasigna. Si un efecto se cae, se marca `caído` y su número queda libre para siempre: quien
  tenía memorizado `S-07` en la gira anterior tiene que encontrar ahí lo mismo, o nada.
- **El mismo efecto puede sonar en varias escenas con cues distintas** (el cue de la 01 y el de
  la 11 serán el mismo latido). Lo que se repite es el sonido; el cue es una ocurrencia
  concreta. **Ninguno de los dos números existe todavía:** se asignan cuando esas escenas
  pasen la puerta, y no tienen por qué ser consecutivos.

  El latido es el caso límite: **mismo archivo, misma cadena, mismo ajuste**, lanzado dos veces
  en la obra. No hay dos tratamientos del mismo sonido —lo que cambia entre la 01 y la 11 es
  todo lo que hay alrededor—, y aun así son dos cues. Ese es el caso raro que la regla tiene que
  cubrir: por eso dos cues y no uno.

### No se inventa el sonido

La misma regla que las letras y que los datos de la banda, aplicada a los efectos:

- Si un sonido no está en la sinopsis, en el autor o en `audiovideo.md`, se marca
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
  se va alPause accidental. Cada cue lleva su forma de parada en `audiovideo.md` (choke group,
  Launch Mode, corte manual) y el operador la tiene que tener a mano.
- **Los cues del disco duran lo que dura la pista.** Si una escena usa «Está bien» entera, el
  cue dura 3:17. Para cortar antes hace falta un segundo cue. `TODO(preguntar):` si hay alguna
  escena donde la música tenga que entrar o salir dentro de la pista.
- **Los vídeos se disparan desde aquí, igual que los sonidos.** El autor decidió el sistema de
  vídeo de la obra (2026-09-28): el «8 mm» es un proyector de vídeo normal disfrazado —no hay
  película de verdad—, los vídeos se lanzan desde Ableton hacia TouchDesigner por OSC o MIDI, y
  Ableton construye también la red de TouchDesigner. Cada proyección es su propio cue `V-nn`, lo
  dispara el operador desde la misma mesa y en el mismo momento que el sonido que la acompaña.
- **Nada de esto se decide aún en el Set.** La arquitectura concreta (pistas, buses, Launch
  Modes, choke groups, key mapping) está en `recursos/audiovideo.md` y se escribe cuando empiece
  el trabajo de sonido.
