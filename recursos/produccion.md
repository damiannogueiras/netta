# Producción

> Calendar, presupuesto, derechos, y todo lo que hace que la obra exista fuera del papel.
>_zona sin dueño por ahora (ver AGENTS.md). Si alguien lo escribe, lo toma._

## Qué hay aquí

Lo que no es el texto y no es la implementación técnica. Lo que responde a preguntas de
«¿esto existe? ¿quién lo hace? y si falla, ¿qué hacemos?».

**No es de aquí** lo que va en otro sitio, aunque se parezca:

| La pregunta | Va en |
|---|---|
| ¿De qué está hecho el Sombrerero y cómo se manipula? | `recursos/fichas.md` |
| ¿Cómo suena ese efecto en Live? ¿Qué cue tiene? | `recursos/audiovideo.md` |
| ¿Qué se ve en la escena 06, cuánto tarda la transición? | `recursos/escena.md` |

## El puesto de operación

> **Estado:** decidido en parte. El hardware de la consola es
> `TODO(preguntar):` — ver abajo. La arquitectura de capas es la propuesta
> de este fichero, sin validar.

### Lo que sí está decidido

- **Un Mac mini en escena**, con Ableton Live y TouchDesigner.
- **El operador dispara a mano**, siguiendo a la manipulación, no un reloj. Eso viene de
  `AGENTS.md` y no se toca: no hay modo automático de escenas.
- **Un Launch por cue**, y cada cue tiene que poder callarse.

### El problema concreto

Alrededor de treinta cues, repartidos en tres actos, en una obra de una hora. El operador
también está manipulando un títere: **no está mirando la consola**. De ahí salen las cuatro
cosas que la consola tiene que cumplir, y que mandan sobre qué se compra:

1. **Que se vea lo que está sonando.** Sin esto el operador tiene que acordarse de qué tiene
   que parar, y en una sala ruidosa eso es pedir un accidente.
2. **Botones grandes**, porque se pulsan de reojo.
3. **Que no se pueda romper nada por error.** Sin cambios de parámetro, sin scrolls, sin un mute
   que se caiga.
4. **Confirmación de dos clases**: un click y una luz. En una sala con sonido, el sonido es la
   confirmación; el vídeo y la luz necesitan la suya.

### La propuesta: tres capas que degradan

La idea no es tener *la* consola, es tener **tres**, de manera que si se cae una quedan las
otras dos. La siguiente es la que está en uso; las de abajo están siempre vivas.

| | Qué es | Cuándo se usa | Si falla |
|---|---|---|---|
| **1. Panel** | Un panel web en TouchDesigner, en la red local, abierto en una tablet. Un botón por cue, ordenado por escena, y **encendido cuando el cue está sonando**. | El 95% del tiempo | Pasa a la 2 |
| **2. Teclado** | Un teclado MIDI por USB **cableado** a un Ableton Live con el Set y el mapa de teclas. Solo los cues imprescindibles. | Los cues estructurales: arranque de escena, apagón final | Pasa a la 3 |
| **3. Pie** | Un pedal MIDI cableado. «Cortar todo» y «siguiente». Sin pantalla, sin red, sin estado. | Cuando la mano está ocupada o algo se ha roto | No hay más capas |

**Por qué el panel en TouchDesigner y no en otro sitio:** es la única de las tres que puede
enseñar el estado. El botón encendido es lo que convierte una lista de treinta botones en algo
que se puede usar sin mirar.

**Por qué el panel y no una Launchpad:** una Launchpad de Novation (~150 €) muestra el estado
de Live, y está bien, pero no sabe nada de TouchDesigner, que es donde vive la mitad de los
cues. Habría que mirar dos sitio. Y no cabe en la decisión de que Ableton es quien manda.

**Por qué un pie y no solo un panel:** un pedal no tiene estado que se pueda desincronizar, ni
red, ni batería, ni pantalla. Es lo más aburrido del mundo y por eso sobrevive a la noche.

### El punto que hay que decidir antes de comprar nada

> **TODO(preguntar):** el panel web vive en TouchDesigner, así que para encender un cue de
> audio **TouchDesigner tiene que mandarle MIDI a Ableton**. Pero en `AGENTS.md` está escrito lo
> contrario: que los vídeos los lanza Ableton hacia TouchDesigner.
>
> Las dos cosas no pueden ser verdad a la vez, y **la diferencia no es solo de quién habla con
> quién**: cambia quién es el que sabe qué se está emitiendo.
>
> Con el panel encima, Ableton deja de poder ser el que manda sin perder el control, y se
> invierte la flecha. Hay que elegir una de las dos:
>
> - **Ableton manda**: la flecha es la de `AGENTS.md`, y el panel tiene que ser otra cosa
>   (Live no tiene panel web propio, y habría que montarlo con una pieza intermedia).
> - **TouchDesigner manda**: el panel es la forma natural de hacerlo, la flecha se invierte, y
>   queda escrito en `AGENTS.md` y en `audiovideo.md`.
>
> Hasta que se decida, **nada de esto está comprado**.

## Si algo falla

Los fallos de verdad en un teatro no son los raros, son los aburridos.

| Qué pasa | Qué se nota | Qué se hace |
|---|---|---|
| **Se va la luz** | El Mac mini y la tablet se apagan | **UPS.** Es la medida que evita la mitad de esta tabla, y la más barata |
| **La tablet se queda sin batería o pierde la red** | El panel se va | El teclado de la capa 2, que va por USB y no depende de nada |
| **El Mac mini se cuelga** | No hay sonido ni vídeo | Reiniciar y reabrir el Set. **Ver abajo: el Set tiene que reabrirse en un estado conocido** |
| **Live se cuelga y TD sigue** | Se pierde el audio, el vídeo sigue | Reiniciar solo Live |
| **TD se cuelga** | Se pierde el vídeo | Reiniciar TD. **El vídeo perdona más que el audio**: el público tarda un segundo en darse cuenta |
| **Se dispara el cue equivocado** | Sonido donde no toca | Todo cue con parada, y un pedal de «cortar todo» |

**Lo que hay que ensayar no es la obra, es el fallo.** Una vez, con calma, en el local: matando
Live, apagando la tablet, desenchufando el Mac mini. El operador tiene que poder volver a estar
en pie con sonido en menos de un minuto, y eso solo se consigue si se ha hecho antes con nadie
mirando.

## El Set tiene que reabrirse en un estado conocido

> **TODO(preguntar):** el punto donde la producción se cruza con la implementación. La
> implementación es de Ableton (`recursos/audiovideo.md`); la decisión de qué se guarda y cuándo
> es de producción.

Antes de empezar la función, el Set se guarda y se queda **guardado, cerrado y con un estado
sabido**. Si Live se cuelga, se vuelve a abrir lo mismo y suena lo mismo.

El fallo que hay que evitar: el guardado automático de Live. Si se cuelga después de un guardado
automático, al reabrir se vuelve a un punto en mitad de la obra, y el operador tiene que saber
en qué punto está para no perder el hilo. Mejor reabrir siempre el principio.

## Lo que falta decidir

- `TODO(preguntar):` **qué consola** — tablet, Launchpad, o las dos. Depende de la flecha
  TouchDesigner/Ableton de arriba, así que no se compra nada antes.
- `TODO(preguntar):` **si el Mac mini lleva pantalla** en escena o va sin ella. Si va sin ella,
  la capa 1 deja de ser un refuerzo y pasa a ser la única forma de ver qué suena.
- `TODO(preguntar):` **la red**: la tablet y el Mac mini en una red propia, no en la del local.
  Una red de invitados se cae justo cuando hay cuarenta móviles en la sala.
- `TODO(preguntar):` **la tablet en la sala**: va con Guided Access activado, en un soporte, cargando
  todo el rato, y con el brillo que se vea desde el puesto del operador y no más.
