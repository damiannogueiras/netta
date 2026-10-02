---
name: construir-sonido
description: Procedimiento para construir UN clip de la obra —un efecto, un pitido, una variación de música, un vídeo— y asignarle su número. Úsalo cuando una escena ya está en `revisada` en `guion/escaleta.md` y toca construir su material, o cuando hay que corregir un clip que ya estaba construido. NO lo uses para escribir el texto de una escena, ni para decidir la arquitectura del Set, ni cuando la puerta está cerrada.
---

# Construir un sonido

Es la contraparte de `cerrar-escena`. Aquella cierra la escena; esta construye lo que la escena
necesita. **Un sonido por sesión, por el mismo motivo que una escena**: el número depende del
estado que dejó la anterior.

## La puerta, y no es un trámite

```
idea → boceto → revisada → cerrada
```

**Antes de nada:**

```bash
grep '| NN |' guion/escaleta.md
```

Si la fila no dice `revisada`, **no construyas nada**. Ni un clip, ni un número, ni una prueba.

El motivo es concreto, y no es un tecnicismo:

> Un efecto construido sobre un texto que se va a reescribir es un efecto que hay que tirar y
> volver a hacer, **con su número gastado** — y los números no se renumeran ni se reutilizan
> nunca. Ese número queda libre para siempre, y quien lo memoricó en otra gira tiene que
> encontrar ahí lo mismo, o nada.

**Excepción: la arquitectura del Set.** Crear una pista, un grupo o un Return **no gasta
números** y no depende de ninguna escena. Eso sí se puede hacer con la puerta cerrada, y está
decidido en `recursos/audiovideo.md`.

## Los tres pasos

### 1. Leer la escena, no el resumen

```bash
cat guion/escenas/NN-nombre/libreto.md
cat guion/escenas/NN-nombre/material.md
```

`libreto.md` es de Guion y es el **qué**: la acotación dramática. `material.md` es tuyo y es el
**con qué**: lo que ya se decidió de esa escena. **Los dos hacen falta, y el primero manda.**

Si `material.md` no existe, créalo. Es la primera vez que se toca esa escena y ese fichero nace
con la estructura de `01-el-corazon/material.md`, que es el modelo.

**Y una cosa que se comprueba aquí:** el libreto tiene que tener marcas `>>`. Si no las tiene, no
sabes qué es diálogo y qué es efecto, y no puedes construir. Se avisa a Guion y se para.

### 2. Escribir el material, en `material.md`

Antes de construir hay que **dejar escrito qué se va a construir**, porque el número se asigna al
escribir, no después:

| Qué | Dónde va en `material.md` | Qué número |
|---|---|---|
| un efecto | «Qué suena» | `S-nn` |
| una variación de música | «La música» | `M[tt-vv]` |
| un vídeo | «Qué se ve» | `V-nn` en TouchDesigner |

Y en cada uno: **la pista donde vive, el Launch Mode, y de dónde sale el material.** Si de dónde
sale el material es «todavía no lo sé», **no se construye**: es una pregunta, y va al `TODO`.

### 3. Construir, y solo entonces numerar

El orden importa: **primero el sonido, después el número.** Si construyes antes de tener escrito
qué es, el número se gasta en algo que no sabes qué es.

**Numeración:**

- **`S-nn`**, efectos y pitidos. `nn` es correlativo, **empieza en 01**, y se asigna **en el
  orden en que las escenas llegan a `revisada`**, no en el orden de la obra. Espera: si la 12 se
  revisa antes que la 05, la 12 se lleva los números bajos. No es un error; el número identifica
  un sonido, no su posición.
- **`M[tt-vv]`**, variaciones musicales. `tt` es el número de pista del disco y coincide con el
  prefijo del fichero. `vv` empieza en `01`, que queda **reservado al original sin tocar**, así
  que la primera variación construida es `vv=02`.
- **`V-nn`**, vídeos. **No es un clip:** es un parameter de TouchDesigner. Lo que se pulsa en Live
  es un **clip MIDI `S-nn`** que manda OSC por `td-osc`.

**El número va en el nombre del clip**, escrito en la Session View, para que se vea en la
pantalla. En el panel también. En `material.md` y en la libreta de registro.

## Antes de dar un sonido por bueno

- [ ] **Se parece a lo que el libreto pide**, no a lo que es técnicamente bonito. La escena dice
      «un pitido como cuando hay una parada cardíaca»: eso no es una alarma.
- [ ] **Tiene forma de callarse.** Un efecto sin forma de parar se acaba en el Pause accidental,
      y en un escenario hay que hacerlo sin mirar. Launch Mode, choke group, o corte manual.
- [ ] **Su nombre es el mismo en tres sitios:** el clip, el botón del panel y el parámetro de
      TouchDesigner. Si se llaman distinto, el operador lanza una cosa y suena otra.
- [ ] **Está el material resuelto.** Si viene de un fichero, está el fichero. Si hay que
      grabarlo, está grabado. Si hay que fabricarlo, está fabricado.
- [ ] **No suena nada que no le toca.** Las 69 pistas de un stem no se abren para hacer una cosa.

## Lo que no se hace aquí

- **Nada de inventar el material.** Si un efecto usa un fragmento de canción, es un fragmento y se
  cita. Si no se sabe de dónde sale el sonido, se pregunta: un efecto inventado se representa
  mañana y no funciona pasado mañana.
- **Nada de números nuevos por corregir.** Si el sonido cambia, es otro clip: el viejo se marca
  `caído` y el nuevo coge el siguiente número libre. Nunca se renumera.
- **Nada de arquitectura.** Pistas, buses, retornos y el panel están decididos en
  `recursos/audiovideo.md`, y cambiarlos es otro encargo.
- **Nada de construir en dos sitios.** Un `S-nn` en un grupo y el mismo número en `audiovideo.md`
  es un número con dos verdades. El número vive en `material.md` de su escena.

## Dónde queda lo escrito

```
guion/escenas/NN-nombre/
├── libreto.md      el texto y las acotaciones          → Guion
└── material.md     los sonidos, los vídeos, la música,
                    los números, los prompts y los TODO → Ableton
```

Y el método, en `recursos/audiovideo.md`: vocabulario, reglas de numeración, el Set y el panel.

## Lo último

**Stagea fichero a fichero**, nunca `git add -A`: en un árbol con tres sesiones, `-A` se lleva
puesto también lo que otra sesión tiene a medio escribir. Y si un cambio no es tuyo, no lo
commitees: repórtalo.

El mensaje del commit nombra **qué ha cambiado**, no la unidad de trabajo: `material 01: las
guitarras solas, con su prompt`, no `avances`.