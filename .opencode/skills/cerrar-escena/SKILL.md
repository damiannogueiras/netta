---
name: cerrar-escena
description: Protocolo para llevar una escena del libreto hasta revisada y cerrada. Úsalo cuando el texto de una escena esté terminado y haya que darla por revisada —actualizar los sitios donde vive el estado, mandar a Ableton la lista de sonidos con las cinco cosas, y commitear— o cuando haya que corregir una escena ya revisada. No lo uses para escribir el texto: para eso se abre la escena.
---

# Cerrar una escena

Una escena se cierra en varios sitios a la vez, y basta con olvidar uno para que las tres
sesiones se desincronicen. Esto es el orden.

**`AGENTS.md` es la autoridad.** Si algo de aquí lo contradice, manda `AGENTS.md` — y
corrige esta skill si hace falta. Relee su sección «El protocolo: `revisada` es la
puerta» antes de empezar; aquí solo está el checklist, no la teoría.

**Una escena por sesión.** La escena N depende del estado que dejó la N-1.

## La puerta

```
idea → boceto → revisada → cerrada
```

El texto se escribe en `idea` y en `boceto`: es lo que hace avanzar a la escena. `revisada`
quiere decir que el texto está y **ya no se toca**.

**Hasta que la escena está en `revisada`, no se le manda nada a Ableton.** Ni los efectos,
ni las pistas, ni un detalle. Ableton no sabe que la escena existe. Si envías algo antes de
la puerta, has construido sobre un texto que se va a reescribir.

## 1. El estado vive en tres sitios

No es un fichero: son tres, y los tres tienen que decir lo mismo.

| Dónde | Qué se toca |
|---|---|
| `guion/escenas/NN-nombre/libreto.md` | La cabecera: `> **Estado:**` |
| `guion/escaleta.md` | La fila de la escena en la tabla, columna **Estado** |
| `guion/escaleta.md` | El bloque `## Estado` del final, que resume los recuentos |

El tercero se olvida siempre, y es el que se lee primero. Si pasas la 05 a `revisada`,
el resumen que dice «Sin escenas `revisada`» pasa a ser mentira.

La **escaleta es la única fuente de verdad**: para comprobar el estado de una escena,

```bash
grep '| 12 |' guion/escaleta.md
```

### `README.md` no existe

El flujo de trabajo de `AGENTS.md` pide actualizar «su fecha en `README.md`», pero el
fichero **no existe y nunca ha existido** (no está en la historia de git). No lo crees por
tu cuenta ni lo des por hecho: es decisión del autor, y lo que puede ser es de **Datos**.

Mientras tanto, el paso queda así: **anota en el `## Estado` de la escaleta la fecha de
hoy** en la línea de la escena que se cierra, y sigue. Cuando el autor decida qué es
`README.md`, se traslada.

## 2. Los sonidos, después de la puerta — no antes

Solo si la escena nombra sonidos. **Nombrar un sonido en el libreto y encargarlo a Ableton
son cosas distintas:** el `>>` en el libreto es el nombre tal como lo oye el público, y se
escribe desde el primer día, pero el encargo se manda al pasar a `revisada`.

**No asignes números de clip.** Los `S-nn` los pone Ableton en `recursos/audiovideo.md`, en el
orden en que las escenas llegan a `revisada`, no en el orden de la obra. Si escribes un
`S-nn` en el libreto, está mal. Los `M[tt-vv]` (variación de pista del disco) sí van en la
escaleta, cuando la variación está construida; en el libreto va solo el nombre en palabras.

Al hilo de Ableton (`1553736444798042246`), con las **cinco cosas**. Si le falta una, no
puede empezar:

1. **Qué escena y en qué estado.** «Escena 12, `revisada` esta tarde».
2. **Qué necesita.** El efecto o la pista, con su nombre tal como lo escribió Guion.
3. **Dónde y cuándo.** En qué punto de la escena, y en qué momento.
4. **Por qué en ese momento.** Qué le pasa a la escena, a la imagen o al público justo ahí.
5. **De dónde sale el material.** Archivo, pista del disco, grabación que hay que conseguir,
   o algo que hay que fabricar. **Si la respuesta es «todavía no lo sé», el material no
   está resuelto** y la puerta no se puede dar por buena: se pregunta antes, aquí o al autor.

```bash
kimaki send --thread 1553736444798042246 --prompt '...'
```

**Dos mensajes por sesión, y a callar.** Al segundo, para. Lo que quede sin resolver se le
pregunta al autor, no se encadena.

Ableton comprueba la puerta antes de empezar. Si le mandas algo de una escena que no está
en `revisada`, lo dice y no lo trabaja.

## 3. El commit

Invoca al sub-agente `@git`, que stagea fichero a fichero y te pide confirmación. Dos
avisos, porque esta escena toca ficheros de más de una sesión:

- La escaleta y el libreto son de **Guion**, tuyos. Si `@git` ve cambios de otra sesión
  —`recursos/audiovideo.md` de Ableton, `investigacion/` o `AGENTS.md` de Datos— **no los
  commitea**: los reporta y te pregunta.
- El mensaje nombra **lo que ha cambiado**, no la tarea: `libreto 12: la cuerda floja a
  revisada`, `escaleta: la 05 entra en revisada`. Los cambios de protocolo, con prefijo
  `git:`.

Si la escena pasa a `revisada` en una sesión que no es la de Guion, el cambio va en su
hilo, no en el tuyo.

## Si vuelve atrás

Una escena que regresa a `boceto` **no mueve los clips que ya tenía**: si el efecto cambia,
el viejo se marca `caído` y el nuevo coge el siguiente número libre. Los números de clip
son sagrados: no se reutilizan, no se renumeran, no se reasignan.

## Lo que no haces aquí

- **No inventes datos** de la banda, del disco ni de las canciones. Si falta algo,
  `TODO(preguntar):` al final del fichero, y pregunta. Una referencia falsa se propaga.
- **No inventes sonido.** Puedes decidir que hace falta un efecto —eso no es inventar—,
  pero no inventar cómo se hace, ni de dónde sale.
- **No toques** `recursos/audiovideo.md`, `investigacion/referencias.md` ni `recursos/fichas.md`.
  Cada fichero tiene un dueño (`AGENTS.md`); si necesitas algo de otro, se lo preguntas al
  autor y lo dices aquí.
- **No abras PR ni push.** Eso es de `@git` y siempre con el autor delante.
