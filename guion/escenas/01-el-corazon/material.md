# 01. Entrada del titiritero — material de sonido

> **Qué es este fichero.** Lo que en la escena 01 **se oye y se ve**: los sonidos, los vídeos y
> las variaciones de música, con sus números cuando los tengan, y los prompts para el agente que
> construye. **Es de la sesión de Ableton.** El texto de la escena es `libreto.md`, y es de
> Guion. Nadie toca el fichero del otro.
>
> **Creado el 2026-10-02** al separar el material por escena. Antes vivía en
> `recursos/audiovideo.md`, que desde ahora es solo el método: vocabulario, reglas de numeración,
> arquitectura del Set y el panel.

## Estado

**La escena está en `boceto`** (`guion/escaleta.md`). **La puerta está cerrada**, así que:

- **Ningún `S-nn`, ningún `V-nn` y ningún `M[tt-vv]` existen.** No se asignan aquí.
- **Ningún prompt de este fichero se ejecuta.** Se escriben para que no se pierdan.
- Los nombres que hay abajo son **nombres de trabajo**, no códigos.

`>>` es lo que se oye, en términos de teatro. Los códigos no van aquí: van en el panel y en la
pista, y no existen todavía.

## Qué suena

| En el libreto | Qué es | Pista | Estado |
|---|---|---|---|
| «Se escucha el latido» | el corazón del titiritero consigo mismo | `latido-suyo` | sin construir |
| «se escucha más vivo y divertido» | el corazón de un niño | `latido-niño` | sin construir |
| «un latido tipo techno, con mucha marcha» | el de un joven. **No es un cuerpo: es una máquina** | `latido-joven` | sin construir |
| «un pitido como cuando hay una parada cardíaca» | **el único que no es un latido** | `latido-parada` | sin construir |
| «empieza lento y luego se acelera» | el de una chica. Con `Repitch` | `latido-chica` | sin construir |
| «suena de fondo «Avivas el fuego», las guitarras, muy limpia y suave» | una variación musical | `mus-guitar` | sin construir |
| el títere habla | su voz | `voz-titiritero` | sin decidir: ¿en vivo o grabado? |
| el títere aparece en una pantalla | un vídeo | `td-osc` → `V-nn` | sin construir |

### Los cinco corazones son cinco clips, y se quedan sonando

Decidido por el autor el **2026-09-30**: *cinco clips de latidos, van sonando según el operador,
quedan en bucle hasta que el operador los para*.

- **`Launch Mode: Repeat` en los cinco**, y **un botón de parada por clip**. No puede ser global:
  en la escena de la parada cardíaca hay que dejar sonar el pitido mientras **vuelve** el latido.
- **Ocho botones en el panel** para el latido: cinco de arranque y cinco de parada. La lista de los botones
  de parada va aquí, no en `audiovideo.md`, que es donde vive la lista del panel.
- **Un clip en bucle tiene que entrar en bucle de verdad**, y un latido es el peor material que
  hay para eso. La cola del prototipo eran 5–7 s; en bucle, esa cola **se enrolla** sobre el
  siguiente latido y suena a *flam*. Por tanto **el largo del clip lo fija el tempo** —un número
  entero de tiempos— y la cola tiene que terminar antes del siguiente golpe.
- **Un bucle tiene que ser aburrido a propósito.** A los cinco minutos el público tiene que poder
  haber dejado de oírlo. Un sonido en bucle que se vuelve interesante se va a notar, y se va a
  notar en la 01, que es donde está el fuego.

### El estetoscopio es un envío, no un bus

El aparato es **de mentira**: nunca lee el corazón de nadie, y **todos los latidos salen de
Ableton**. No hay micro de público ni ninguna fuente real.

Aun así, el estetoscopio **explica de dónde sale el sonido**: un estetoscopio real tiene una
membrana en la campana que se come los agudos y deja el «lub-dub», y por eso un corazón junto a
uno suena así y no como un bombo. Eso hace que **un solo sonido de latido dé las cinco versiones
sin dejar de ser el mismo latido**: la diferencia entre un niño y un joven es el material que
entra filtrado, no cinco efectos distintos.

En el Set eso es el envío al Return `Dentro`, **uno por pista**. Y por ser un envío y no un
device del bus, el estetoscopio es un knob:

- Los tres corazones de verdad mandan al `Dentro`.
- El techno y el pitido pueden mandarlo a cero, y entonces se oyen en la sala —que es lo que
  dice el libreto: que ahí **el estetoscopio miente, y a propósito**.

`TODO(preguntar):` **si la membrana se levanta en esos dos o no.** Todavía sin decidir, y es lo
que hace bien tenerlo como envío: **las dos respuestas cuestan un knob, no una reconstrucción.**

## Qué se ve

- **El titiritero aparece por un fade muy suave en una pantalla.** Eso es un vídeo: una red CHOP
  en TouchDesigner, disparada desde Live por un clip MIDI que manda OSC. El parámetro es un
  `V-nn` y **no existe todavía**; el clip MIDI que lo dispara es un `S-nn`, y tampoco.
- **El negro.** Como la imagen es una proyección, tiene que poder cortarse a negro igual que
  todo el sonido se calla, y con el ruido de un proyector detrás el negro tiene que ser un negro
  de verdad, no el gris de la lámpara.

`TODO(preguntar):` **de dónde sale el vídeo del titiritero.** Si la pantalla es una pantalla, el
titiritero está proyectado —y entonces hay que decidir quién lo dibuja y quién lo graba. Va a
`Datos` por los derechos si sale de un archivo de la banda.

## La música

**Una variación, del «Avivas el fuego»:** *«solo las guitarras, muy limpia y suave, con el latido
debajo»*. Es la que dice la cabecera de la escena, y es la primera construcción que la obra
necesita.

```
M[01-vv]   tt = 01, del «Avivas el fuego»   ·   vv no existe todavía
```

**Los ficheros.** Solo seis, todos en `recursos/musicas/Avivas el Fuego - files/`:

```
GUIT 440 - Comp A combinado_7.wav      ┐
GUIT 441 - Comp A combinado_7.wav      │
GUIT 8 440 - Comp A combinado_7.wav    ├  la parte
GUIT LINE - Comp A combinado_7.wav     │
GUIT ROOM L - Comp A combinado_7.wav   │
GUIT ROOM R - Comp A combinado_7.wav   ┘
```

Cada una tiene además su `_8`. **Los dos comps son grabaciones distintas** —correlacionan al 0,33
a nivel de muestra—, y el `_8` es **más fuerte** que el `_7` en las seis (−25 dBFS el `_8` de la
440 frente a −29 el `_7`). **Cuál vale se decide oyendo, no midiendo.** `TODO(preguntar)`.

**Y falta la pregunta que la bloquea entera:** qué son `440`, `441`, `8 440`, `LINE` y `V44`.
Casi seguro son referencias de micrófono o de toma, pero elegir la guitarra «limpia» sin saber si
`GUIT 440` es el micro del amplificador o la entrada de línea es elegir a ciegas. **Lo sabe el
autor, que estuvo en la grabación.**

## Los prompts

Ninguno se ejecuta. La escena está en `boceto`.

### Las guitarras solas — preparado

> **Lo que el prompt tiene que resolver dentro de Live:**
>
> 1. Las seis en **un bus de guitarra con un fader**, no seis faders sueltos. La variación es
>    «mucha guitarra», y eso se controla con un fader de bus.
> 2. **Todo lo demás en silencio, no cargado.** Ni bajo, ni palmas, ni percusión, ni voz. La
>    variación no es «la canción con la guitarra más fuerte»: es la guitarra y nada más, y eso
>    significa que los otros 69 stems no se abren.
> 3. **Un fundido de salida**, porque la escena 11 se apaga con esta canción y los stems duran
>    5:39,4, no 5:45,3.
> 4. **Reservar hueco para el latido debajo.** La escena dice «con el latido debajo», así que el
>    bus de guitarra tiene que dejar sitio en el medio, y **la mezcla no se cierra hasta que no
>    esté decidido el nivel del latido.** Es una decisión de mezcla, no de sonido.
> 5. **Una Launch, un clip, una forma de parar.** Y `Launch Mode: Repeat` con una sola
>    repetición: el clip son 5:39 y la escena dura menos.

> `TODO(preguntar)`: **«muy limpia y suave» no se puede construir todavía.** Los seis ficheros
> son una grabación de estudio, y «limpia» quiere decir **sin reverb**, y no se sabe si la traen
> dentro. El agente tiene que **mirar la cadena de los seis antes de dar por buena la
> variación** — y si los seis ya traen reverb, **se avisa, no se improvisa.**

### La voz sola — no se puede escribir

La escena también dice «la voz sola» en algún punto de su viaje, y **ese prompt no existe**: no
hay voz seca. Los únicos ficheros de voz (`ALEX`, `TANIA`) tienen señal **únicamente** en las
versiones con la Telefunken 51 ya puesta, y no hay forma de quitar una reverb que viene dentro del
audio. Ver `recursos/essentia.md`, «El problema gordo».

`TODO(preguntar)`: que se exporten las voces secas de la sesión de mezcla.

## TODO(preguntar) de esta escena

- **Qué es la guitarra «limpia».** Los números de los nombres. Bloquea `M[01-vv]`.
- **Cuál de los dos comps.** `_7` u `_8`. Se decide oyendo.
- **Si la membrana del estetoscopio se levanta** en el techno y en el pitido.
- **Voz seca**, para que exista «la voz sola».
- **Si el títere habla en vivo o viene grabado.** Cambia el grupo `voz`, no la arquitectura del
  Set. Y si es proyectado, **de dónde sale el vídeo**.
- **El nivel del latido contra el de la guitarra.** Con un iPad en la mano y dos dedos se ajusta
  en diez segundos con la escena delante. Es una decisión de mezcla, y para entonces habrá una
  oreja al otro lado.

Y de Guion, que no es mío pero lo dejo dicho: **el texto no tiene marcas de sonido (`>>`) ni de
luz (`**`)**. Sin ellas no se sabe qué es diálogo y qué es efecto, y la escena no puede pasar la
puerta. Es lo primero que hay que hacer cuando el texto esté cerrado.