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
│   └── libreto.md                 el texto que se representa
├── recursos/
│   ├── musica.md                  cómo se usa el disco: qué pista en qué momento
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
- **`guion/libreto.md`** — el texto en sí, escena por escena, con las acotaciones. Se escribe
  cuando la escena ya está `revisada` en la escaleta; no se escribe a la vez.
- **`recursos/musica.md`** — el mapa pista → escena, con la función dramática de cada
  canción (no solo "suena aquí": por qué suena aquí).
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
2. Trabaja **un fichero por sesión**. Es un proyecto creativo, no una tarea lineal: mezclar
   varias escenas a la vez hace que se pierda el hilo.
3. Cuando se cierre una escena, actualiza su estado en la escaleta **y** su fecha en
   `README.md`.
4. Escribe en el fichero que corresponda, no en uno nuevo. Si un dato no tiene sitio, casi
   siempre es porque falta decidir algo: eso es una pregunta, no un fichero extra.
5. Al final de la sesión, deja escrito lo que has decidido y lo que queda abierto. La
   siguiente sesión no tiene tu contexto.

## Convenciones

- Ficheros y carpetas en minúsculas, sin tildes, con guiones: `musica.md`, `escaleta.md`.
- Las escenas se numeran con dos dígitos: `1.`, `2.`, `10.`.
- Las acotaciones van entre paréntesis: `(el pato gira la cabeza hacia el público)`.
- Los cambios de sonido se marcan con `>>` y los de luz con `**`: `>> un alaseteo`.
- Las preguntas abiertas se dejan como `TODO:` al final del fichero, no interrumpen el texto.
