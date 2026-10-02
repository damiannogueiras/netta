# Audio y vídeo

> **Todo el sonido y toda la imagen de la obra.** La música del disco, los efectos sonoros, las
> proyecciones de vídeo, la red de TouchDesigner y la parte técnica. **Un solo fichero**
>
> **Doce escenas** en tres actos, con la música colocada y el disco cerrando donde abre
> (`guion/escaleta.md`).
>
> **Estado: convención decidida. Set sin construir.** Está escrita la forma de trabajar —qué es
> un clip, cómo se numera, cómo se dispara— y hay **un clip descrito pero sin número** 
>
> **Reparto:** este fichero es de la sesión de Ableton. Lo nombra Guion y lo decide aquí; lo
> anota Datos.

### Qué significa, en la práctica

- **El disco es materia prima, no material de escena.** Lo que suena en la obra no es una pista
  del disco: es una construcción hecha con pistas sueltas de una o varias canciones, con ecos,
  repeticiones, y a veces pasado a MIDI para tocarlo con otros instrumentos.
- **El número de pista del disco deja de identificar lo que suena.** Antes cada pista del disco
  era *una pista entera, un clip*. A partir de aquí un tema es solo *material de origen*, del que
  salen varios sonidos distintos y ninguno de ellos es el original. Los sonidos musicales llevan
  **`M[tt-vv]`**; ver [la serie de la música](#la-serie-de-la-música-mtt-vv).


## La serie de la música: `M[tt-vv]`

> `S[XY-NM]` —tema del disco y variación—, y la `S` se descartó porque **ya significa «efecto
> la letra libre es la `M`. La forma final es **`M[tt-vv]`**: `tt` es el número de pista del
> disco (dos dígitos, siempre con cero delante) y `vv` es el número de variación dentro de ese
> tema. Con esto **la letra siempre dice el tipo**: `S` efecto, `M` música, `V` vídeo.

```
M[01-03]   →   «Avivas el fuego» (pista 01), variación 03
```

### Qué identifica

**Un `M[tt-vv]` es un sonido musical, y dice de qué tema sale.** Las dos mitades hacen falta
porque el disco es material de origen y no el resultado: el `tt` apunta a la fuente y el `vv`
distingue lo que has hecho con ella.


### Las reglas

1. **`tt` es el número de pista del disco, no un índice de este documento.** `M[01-…]` es el
   tema 01 del disco siempre, y no se renumera aunque las escenas cambien de orden. Por eso el
   formato se parece tanto a un nombre de fichero: es la *dirección del material* —y aquí el
   prefijo y el `tt` son el mismo número, confirmado el 2026-09-29.
2. **`vv` no se reutiliza nunca.** Si una variación cae, su `vv` queda libre para siempre y se
   marca `caído` en la tabla, como cualquier otro clip. La regla de la numeración sagrada
   aplica igual a las dos mitades del código.
3. **`vv` empieza en `01` y sube en el orden en que se construyen las variaciones**, no en el
   orden en que salen en la obra. Como con los `S-nn`, el número identifica un sonido y no su
   posición.
4. **Un tema, una variación: nunca dos temas a la vez.** `M[01-03]` sale del tema 01 y solo del
   01. Decidido por el autor el 2026-09-29: *«no vamos a usar dos temas a la vez»*.
5. **Toda variación lleva nombre.** El código va en la libreta de registro, y un código sin
   nombre no sirve de nada: el operador no puede mirar una tabla para acordarse de qué es
   `M[02-03]`. El **número** es la identidad y no se toca nunca; el **nombre** es lo que se lee
   en el panel, lo que dice el libreto y lo que se busca cuando suena. El prototipo ya
   funcionaba así: `latido-prueba` tenía nombre y no tenía número.

### Por qué la regla 4 importa

Sin ella habría que decidir qué hacer con un sonido hecho de material de dos temas: si manda
el tema principal y el otro va en la tabla, o si el tema compuesto recibe número propio. Con
la regla cerrada, **cada variación es autocontenida**: todo el material de un `M[tt-vv]` está en
la pista `tt` del disco, y buscar de dónde sale un sonido es mirar un número. También evita
una tentación: crossfades entre temas, que con la regla 4 no existen. Un cambio de tema es un
corte entre dos clips, no una mezcla.

> Comprobado contra la escaleta: **ninguna escena usa dos temas.** La 03 no usa disco, y cada
> escena de las demás tiene uno solo. La regla no obliga a cambiar nada de lo escrito.

### `tt-01` es siempre el original sin tocar

Por convención, **`M[tt-01]` es el tema tal cual, sin procesar.** Existe aunque no se use en
ninguna escena, y sirve de referencia: si una variación con ecos y MIDI suena rara, se compara
contra el original y se oye qué ha cambiado. Además da un punto de retorno conocido.

### Lo que queda pendiente

- **Los libretos.** Escriben `>> ♪ «Avivas el fuego» (p. 02)`, y eso está mal por partida doble:
  describe la pista del disco en vez de lo que suena, **y el número tampoco** —Avivas es la 01—,
  así que el `(p. nn)` sobra igual. La convención es que cada variación vaya por su **nombre**,
  sin código y sin número de pista: `>> ♪ «la voz sola, dos veces con eco» (del «Avivas el
  fuego»)`, donde el tema sí se nombra, como nombre. Avisado a Guion; el cambio en sus ficheros
  es suyo y no se toca aquí.
- **La escaleta** recibirá los códigos musicales, pero **no todavía**: ninguno existe. Cuando
  una variación se construya y tenga su `vv`, se añade a la escaleta. Es de Guion, y es el mismo
  trabajo que poner el nombre en el libreto.

### El registro: dónde se mira cada cosa

| | Qué lleva |
|---|---|
| `guion/escenas/NN-*/libreto.md` | El **nombre** de la variación en palabras: `>> ♪ «la voz sola» (del «Avivas el fuego»)`. **Ningún código**, ni de música ni de efecto ni de vídeo: en el libreto solo hay nombres. |
| `guion/escaleta.md` | **Los códigos musicales** `M[tt-vv]`, y solo los musicales, y solo cuando ya existen. Decidido por el autor el 2026-09-29. **Los `S-nn` y los `V-nn` no van aquí**: los efectos y el vídeo se inventarían en este fichero. |
| `recursos/audiovideo.md` | El **registro de los tres**: código ↔ nombre ↔ tema de origen ↔ receta ↔ botón del panel ↔ escenas. **Es la fuente: el número existe aquí y en ningún otro sitio.** La escaleta recibe una copia, y por eso puede quedar desfasada sin que nada se rompa. |

> **Por qué solo la música llega a la escaleta.** La escaleta es un índice, y lo que se busca en
> un índice es *qué suena*. La música es lo que el público oye de continuo y lo que hay que
> situar en el tiempo; los efectos y el vídeo son golpes sueltos que se inventarian aquí. Meter
> cada `S-nn` en la escaleta llenaría un índice de códigos que casi todos todavía **no existen**,
> porque ningún número se gasta antes de la puerta.

> **Un código es una receta, no un clip.** *«La voz sola, dos veces con eco»* no es un clip: son
> dos o tres clips más un retorno de eco. El código identifica **el sonido**, y los clips son
> una manera de construirlo. La consecuencia para el Set es que **no toda variación va a ser un
> Launch**: si necesita varias acciones coordinadas, es el caso de «cadenas de clips» de más
> abajo. Que el código **no separe del número de clips** es justo lo que permite rehacer la
> construcción sin que cambie el código.

## Los cuatro niveles

> **Desde el 2026-10-02 son cuatro, no tres.** La causa: el material de cada escena pasó a su
> propia carpeta, en `material.md`. Y eso parte el eje de la tabla, que antes era «un fichero por
> autor» y ahora **dos de los cuatro son del mismo dueño**.

| | Dueño | Qué lleva | Qué no lleva |
|---|---|---|---|
| `guion/escenas/NN-*/libreto.md` | Guion | Lo que se ve y lo que se oye, en términos dramático-teatrales, con su `>>`. | Nombres de dispositivo, de pista, de efecto, de nodo de TouchDesigner, dB, y **ningún número de clip**. |
| `guion/escenas/NN-*/material.md` | Ableton | **Lo de una escena**: qué suena, qué se ve, qué variación de música, sus números, sus prompts y sus `TODO`. El nombre de la pista donde vive cada clip y su Launch Mode. | La cadena de devices, la automation, los dB. **Y nada de ninguna otra escena.** |
| `recursos/audiovideo.md` | Ableton | **Lo de la obra entera**: la convención, la numeración, la arquitectura del Set, el panel, el flujo entre sesiones. | **Nada de una escena en concreto.** Los prompts y las tablas por escena viven en `material.md`. |
| `AGENTS.md` | Datos | La convención. | Nada del sonido ni del vídeo concretos. |

**El corte que importa ya no es de dueño, es de alcance:**

```
libreto.md      de una escena, escrito por Guion
material.md     de una escena, escrito por Ableton
audiovideo.md   de la obra,     escrito por Ableton
```

Y hay una razón de fondo para que el registro de números viva en `material.md` y no en el
maestro: **el número se asigna cuando su escena pasa la puerta**, así que el número y su escena
no pueden estar en ficheros distintos.

## El Set

**Un Set, un operador, un Launch por clip, y encima un panel de OSC en un iPad.** Decidido por el
autor (2026-09-27 y 2026-09-28).

> **Ableton Live 12.** Confirmado por el autor (2026-09-27). Importa porque los nombres de
> los dispositivos han cambiado entre versiones, y lo que se escriba aquí tiene que existir en
> la versión con la que se va a construir.

### La superficie de control ya está decidida: un panel de OSC en un iPad

> **Decidido por el autor (2026-09-28):** «El sonido, los efectos, la música y los videos los
> lanzaremos desde un panel tipo cliente de OSC en un iPad, lanzaremos indistintamente o
> conjuntamente, cosas en Ableton y en TouchDesigner.»

Esto **cambia lo que estaba escrito aquí**, que era «el operador lanza la Launch en la Session
View». Inside Live no cambia: sigue habiendo un Launch por clip. Lo que cambia es **quién lo
toca**. Y cambia una consecuencia que sí importa:

> **El `S-nn` deja de ser la etiqueta que el operador ve.** Antes, en la Session View a oscuras,
> la rejilla de nombres era la referencia. Ahora el operador ve **el panel**, y el panel es lo
> que hay que diseñar. De ahí salen tres reglas.

1. **El panel es parte de la obra.** Un botón es una pieza de theater, no una interfaz: se lee
   en un segundo, con poca luz, con los dedos y sin mirar fijamente. Su disposición se decide
   con el mismo cuidado que una acotación de manipulación.
2. **Un botón puede ser varias cosas.** «Indefinidamente o conjuntamente» quiere decir que un
   botón puede lanzar un sonido, un vídeo, o los dos a la vez. **Así que un clip ya no es
   necesariamente un sonido**: puede ser un compuesto. Ver «cadenas de clips».
3. **El nombre tiene que ser el mismo en los tres sitios** — el botón del panel, la pista o
   escena de Live, y el operador de TouchDesigner. Tres sitios y un nombre. Si se llaman
   distinto, el operador lanza una cosa y suena otra, y en un escenario no hay segunda
   oportunidad.

> **El panel se documenta en este fichero**, en «El panel». Es la única pieza que ve a la vez a
> Live y a TouchDesigner, y el autor ha decidido que las dos cosas vivan en el mismo fichero, así
> que el panel se queda con ellas. Antes propuse partirlo en `imagen.md` y `panel.md`: **anulado**.

### Cómo se dispara

Cada clip es una escena de Launch en Session View, y lo lanza quien opera siguiendo la
manipulación, no siguiendo un reloj. Con el panel, el Launch se dispara desde fuera: el operador
toca un botón, el botón manda un mensaje, y ese mensaje acaba lanzando el Launch. La consecuencia
no es cosmetic: **el operador ya no ve la Session View**, así que todo lo que necesitaría de
ella —el nombre, el número, el estado, si algo está sonando— tiene que estar en el panel o
deducirse del sonido.

- **La música es manual también.** No hay una Launch por escena de la obra con la música
  automatizada: cada variación musical es su propio clip `M[tt-vv]` y el operador lo lanza. Si el
  títere se retrasa, la variación no se para sola.
- **Cada clip tiene que poder callarse.** Un efecto sin forma de parar se acaba en el Pause
  accidental, y en un escenario hay que hacerlo sin mirar la pantalla. Cada clip lleva su forma
  de parada escrita en su fila: *choke group*, *Launch Mode: Gate/Toggle*, corte manual, o lo
  que toque.
- **Una variación musical dura lo que se construya, no lo que dura la pista.** La p. 09, «Está
  bien», son 3:23 en la mezcla, pero `M[09-02]` puede ser 20 s. La duración la decide la variación, y por eso **no se
  sabe todavía si alguna necesita un segundo clip con un corte**: depende de cómo se construya.
- **Con el panel, el corte tiene que ser un botón.** Si el operador no ve la Session View,
  entonces *cada* clip necesita su forma de parada **en el panel**, o el corte se hace a ciegas.
  **Resuelto el 2026-09-30: un botón de parada por clip, y no puede ser global.** Ver «Los cinco
  clips laten en bucle», donde está el porqué —con un latido en bucle, cortar «todo» a la vez
  impide que el latido vuelva mientras se oye el pitido.

### cadenas de clips: cuando un botón lanza de las dos máquinas

Un botón del panel puede lanzar un `S-nn` y un `V-nn` a la vez. Eso está bien y es lo que hace
que sincronía no sea un problema. Pero hay un caso que no es un Launch:

**Lo que pasa dentro de una pista larga no se puede lanzar.** En la 02, «Está bien» entra y a
mitad de escena **la música se relentece, el proyector echa humo y la película se quema**: tres
cosas dentro de una variación musical. Un Launch no sirve, porque el operador no puede disparar
algo «a la 1:47» sin mirar, y aunque lo hiciera, la noche siguiente no cae en el mismo sitio.

Hay tres salidas, y solo una es segura:

| | Cómo | Cuándo sirve | Riesgo |
|---|---|---|---|
| **1. Todo colgado del transport** | TouchDesigner sabe en qué punto va la pista y dispara solo lo que toca en ese punto | la imagen cae en el compás, cada noche, sin que nadie piense | hay que mandar **la posición** de Live a TD, y MIDI no la manda |
| **2. Todo en un clip largo** | el vídeo es un clip largo que contiene la escena entera, quemado incluido | no hay nada que sincronizar porque no hay dos cosas | se pierde la posibilidad de parar y arrancar por partes |
| **3. A ojo, el operador dispara** | el operador lanza el quemado cuando le parece | en un ensayo | **no es repetible delante del público**, y en la 02 el quemado es el evento de la escena |

La 1 es la buena, y por eso el protocolo de la escaleta («los vídeos se lanzan desde Ableton
hacia TouchDesigner por **OSC o MIDI**») tiene que ser **OSC**: **MIDI lleva reloj, no lleva
posición.** Un mensaje MIDI no puede decir «van por el 1:47». Uno OSC sí. `TODO(preguntar):` la
dirección, y ver «El panel» para la topología.

#
---

---

# El vocabulario

> **Decidido por el autor el 2026-09-30:** la documentación y las conversaciones usan **los
> términos de Ableton Live 12 y de TouchDesigner**, no palabras propias. La palabra con la que
> aquí se llamaba «el sonido que se lanza» queda **retirada**, y en su lugar se usa **clip**.

**Live no tiene ninguna palabra para eso.** Lo más parecido que hay en el manual es una función
de **monitoreo por auriculares**: el interruptor del Main track que sustituye el Solo de cada
pista por un botón con auriculares y manda esa pista a una salida aparte, para oírla sin que la
sala la oiga. No es lo mismo en absoluto, y por eso la palabra no se podía seguir usando aquí.
Y esa función nos viene bien además: el operador puede comprobar un clip en auriculares antes de
subirlo al crossfader. Es distinto de todo lo de aquí.

## Ableton Live 12

| Término | Qué es en Live | Qué es en la obra |
|---|---|---|
| **Clip** | porción de audio o MIDI en un clip slot, con su Launch Mode y su nombre | **una unidad de sonido.** Cada sonido que lanza el operador es un clip. El nombre del clip **es** su identificador, así que `S-07` se escribe en el clip de la Session View y no en un fichero aparte |
| **Clip Slot** | la celda de la Session View | un sonido por celda. La posición en la rejilla es lo que permite encontrarlo en un segundo, y la hipótesis más limpia para el panel del iPad es que sea una copia de la Session |
| **Track** | el canal. Hay **Audio**, **Instrument** (nuevo en 12), **Group**, **Return** y **Player** (nuevo en 12, reproduce archivos sin warp) | un canal por familia: corazón, guitarra, percusión, voz, vídeo. **Group = el bus**, y es donde vive el fader que pide el libreto («solo las guitarras», «muy suave»): un clip tiene volumen, una variación tiene nivel. **Player** es el tipo que corresponde a los stems |
| **Launch Mode** | **Trigger**, **Repeat**, **Alternate**, **Gate** | cómo se para cada clip. Es la respuesta a «cada clip necesita poder callarse». **Gate** es el modo del latido: se corta en caliente sin recalentrar nada |
| **Stop Clip** | el clip de parada al final de una cadena de una pista | la forma de callar todo lo que hay detrás |
| **Set** | el fichero de sesión, el `.als` | **uno solo**, abierto antes de empezar y no recargado durante la función |
| **Crossfader** | las transiciones entre pistas, con los botones A y B de asignación | los relevos entre sonidos |
| **Fila** | lo que el manual llama *Scene*: una fila de la Session View | **no es una escena de la obra.** Decidido el 2026-09-30: la fila de Live se llama **fila**, y «escena» queda solo para la obra. Sin eso, «la escena 05» y «la fila 5» serían lo mismo en la misma frase |

## TouchDesigner

| Término | Qué es | Qué es en la obra |
|---|---|---|
| **Component** | cada proyecto de TouchDesigner | uno para la red entera |
| **Perform Mode** | el modo de actuación, donde solo se ven los controles | el modo en que está la máquina durante la obra |
| **Parameter** | un control con nombre, con su propio panel | **cada vídeo es un parameter.** Es el `V-nn` |
| **CHOP** | la cadena que procesa vídeo | un vídeo = una red CHOP: Movie In → Transform → Composite → Movie Out |
| **OSC In** | la puerta por donde Live manda un disparo | el mensaje que enciende un parameter |
| **Panel** | una ventana de controles que se puede mandar a otra pantalla | el panel del iPad |

## Lo que se deja de decir, y por qué

| Palabra | Por qué se va |
|---|---|
| **la palabra retirada** | aquí era «el sonido que se lanza», y eso en Live es un **clip**. En Live lo más parecido es el monitoreo por auriculares, que es otra cosa |
| **launch** | «el launch» sonaba a evento, y es un **clip** que se pulsa. Se reserva «lanzar» para la acción, no para el objeto |
| **P-nn**, y decir «serie» de sonidos | `S` y `V` y `M` **siguen**, pero identifican **clips y parameters**, no sonidos. El número no se reutiliza igual, por el mismo motivo |
| **«compuestos»** | era un botón que lanzaba varias cosas. En Live es un **clip MIDI** cuyo Launch Mode es lo que coordina, o una cadena de clips. Ahora es una **cadena de clips** |
| **«serie»** | sigue haciendo falta, pero es de **objeto**, no de palabra: la serie `S` son clips de audio, la `M` son clips musicales, la `V` son parameters de TD |

## Y el identificador, que es lo que cambia de verdad

**El código va escrito como el nombre del clip en la Session View.** No en un fichero aparte, no
en un panel aparte, no de memoria. `S-07` es el nombre de un clip que el operador ve en la
pantalla. Y `M[01-02]` igual.

Eso no cambia la numeración sagrada ni una coma: sigue sin reutilizarse, sin renumerarse y sin
reasignarse. **Lo que cambia es dónde se mira.** Antes el número vivía en este fichero y el
operador tenía que venir aquí a recordarlo; ahora vive en la pantalla, que es donde lo busca
siempre.

Y un aviso que sale de aquí, porque es una trampa fácil: **`V-nn` no está en Live.** Es un
parameter de TouchDesigner. El clip MIDI que lo dispara es un `S-nn` y sí está en la Session View.
Ver «`V-nn` no es un clip».

# Los prompts preparados
## Desplegar el Set en la otra máquina

> **Este prompt no construye sonidos: construye la arquitectura.** No gasta ningún número de
> clip, no toca ninguna variación musical y no necesita que ninguna escena haya pasado la puerta
> `revisada` — la puerta protege **los números y los clips**, y esto son pistas, grupos y un
> Return. Se puede hacer hoy. La 01 sigue en `boceto` y eso no lo impide.
>
> **A quién va:** el agente que tiene el MCP y Live abiertos, en la otra máquina. Este no es el
> hilo de Guion ni el de Datos; es una máquina con Ableton y TouchDesigner, que es donde se
> despliega.

Copia y pega tal cual:

```
Voy a desplegar la arquitectura de un Set de Ableton Live 12 en esta máquina. No construyas
ningún sonido todavía: solo los contenedores. Contexto completo antes de nada.

## Lo que no es este encargo

NO construyas ninguna variación musical. NO asignes ningún S-nn ni ningún M[tt-vv]. NO
construyas el latido, ni la membrana, ni la guitarra. Esto es un Set vacío con los buses puestos.
El motivo es que las escenas no han pasado la puerta y los números son sagrados: un clip que se
construye sobre un texto que se va a reescribir es un número que se gasta para siempre.

## Cómo se llama cada cosa, y por qué importa

En nuestra documentación, FILA es lo que el manual de Live llama "Scene": la fila de la Session
View. ESCENA es una escena de la obra de teatro y no tiene nada que ver. Si en tu respuesta
"escena" y "fila" significan lo mismo, has fallado.

Una PISTA es una familia de sonidos. Un CLIP es un sonido. El identificador de un clip
(S-nn, M[tt-vv]) es el NOMBRE del clip, escrito en la Session View, no un código de libro.
V-nn no es un clip: es un parameter de TouchDesigner.

## Lo que hay que crear

1. Un grupo (Group track) llamado `latido`. Sin ningún device encima: este bus es NIVEL, y nada
   más. De él cuelgan cinco pistas.

2. Cinco pistas MIDI que cuelguen de `latido`, en este orden:

   - `latido-suyo`
   - `latido-niño`
   - `latido-joven`
   - `latido-parada`
   - `latido-chica`

   Deja las cinco vacías, sin rack. Se llenarán cuando el latido se construya.

3. Las cinco mandan un envío a un Return que viene en el punto 5. El envío lo usan las tres
   primeras; las dos últimas pueden no mandarlo, porque el estetoscopio miente a propósito en
   esos dos momentos. El nivel del envío no lo decidas tú: se decide mezclando, y todavía no
   hemos decidido si la membrana se levanta en esos dos o no.

4. Un grupo (Group) llamado `musica`, con un compresor como red de seguridad. NO un sidechain:
   el ducking lo hace el operador con los dedos, y el compresor está para que a nadie se le
   escape un latido, no para hacer el trabajo del ducking.

5. Un Return (Return track) llamado `Dentro`, con un Reverb como punto de partida. Este es el
   bus del estetoscopio y del cuerpo. Va vacío de momento: la membrana se construye con el
   sonido delante.

6. Un grupo llamado `voz`, con una pista de audio dentro llamada `voz-titiritero`, con la
   entrada 1 asignada al micrófono. La cadena, vacía.

7. Un grupo llamado `escena`, vacío. Es para lo que suene de principio a fin: aire, sala,
   onomatopeyas. No le pongas nada.

8. CINCO pistas de Player, una por familia de instrumento, todas dentro de `musica` y todas
   vacías:

   - `mus-guitar`      (GUIT 440, 441, 8 440, LINE)
   - `mus-bajo`        (BASS DI, BASS PEDALES)
   - `mus-percusion`   (DARBOUKA, TOM, CAJA, SHAKER, RIDE, SNR, HH, KICK)
   - `mus-palos`       (Palmas)
   - `mus-aire`        (ROOM L/R, ROOM 58, GOLIAT, OH L/R, Audio 164)

   Es una pista por FAMILIA, no por canción. La misma pista toca los nueve temas del disco; lo
   que cambia de una escena a otra es el clip, no la pista.

9. Una pista MIDI llamada `td-osc`, FUERA de todos los grupos, que es la única que habla con
   TouchDesigner. Encima, un dispositivo de Max for Live que mande OSC: un clip MIDI por cada
   vídeo, y cada clip manda el OSC de su V-nn. Esto es lo único que no es audio, y es lo que
   hace que los vídeos se puedan lanzar desde el panel del iPad.

## Lo que tienes que hacer si algo no existe

- Si no hay Max for Live, NO inventes una manera de mandar OSC: dilo y para. Sin M4L no hay
  vídeo desde el panel, y eso es una decisión, no un rodeo.
- Si en esta versión los Player tracks no existen, o no se llaman así, usa Audio tracks y
  anótalo en el informe.
- Si alguno de los nombres choca con algo que ya existe, no lo renombres en silencio: dímelo.

## Lo que quiero de vuelta

Una lista, en este orden:

1. Los grupos, las pistas y los retornos que has creado, con su orden.
2. El enrutado: qué va a dónde, y qué envíos existen.
3. Los Launch Mode de cada clip que hayas puesto. Ninguno, si no has puesto ninguno. Si decides
   crear clips vacíos en las cinco pistas de latido para verlos, con Launch Mode Repeat y un
   nombre de trabajo SIN número, dilo también.
4. Lo que no se ha podido hacer, y por qué.
5. Una captura de la Session View, si puedes.

## Y antes de nada, una pregunta

¿Esta máquina tiene Ableton Live 12 abierto, con un Set vacío, y responde el MCP de
workspacemcp? Si el MCP no responde, no hagas nada de lo de arriba y dímelo: son cambios que no
se pueden deshacer a distancia, y un Set a medio construir es peor que un Set vacío.
```


> **Ninguno de estos se ha construido.** Se escriben aquí para que no se pierdan y para que
> estén listos el día que la puerta se abra. **La puerta está cerrada:** la escena 01 sigue en
> `boceto` (`guion/escaleta.md`), y `AGENTS.md` dice que hasta `revisada` no se le pasa nada a
> Ableton. Escribirlos aquí no gasta número: **el `vv` se asigna el día que se construya**, y por
> eso ninguno lleva código todavía.

## Los prompts de cada escena, en su escena

Desde el **2026-10-02** los prompts no viven aquí. Cada escena tiene su material en su propia
carpeta, junto al libreto:

```
guion/escenas/01-el-corazon/
├── libreto.md      el texto          → Guion
└── material.md     lo que se oye y
                    se ve, y los
                    prompts           → Ableton
```

Dos ficheros, dos dueños, una carpeta. Los números de clip van en `material.md` de su escena, y
esa es la razón del reparto: **el número se asigna cuando su escena pasa la puerta**, así que el
número y su escena tienen que vivir en el mismo fichero.

- **`material.md` es de Ableton.** Contiene los sonidos, los vídeos, las variaciones musicales,
  los prompts y los `TODO(preguntar)` de esa escena.
- **`libreto.md` es de Guion.** Nadie toca el fichero del otro, ni aunque estén en la misma
  carpeta.

**Los prompts que no son de ninguna escena se quedan aquí**, porque son de la obra entera y no de
una: el de desplegar el Set es el caso. Nació aquí y aquí vive.

## El panel

`TODO(preguntar):` **dónde vive.** Y qué es exactamente: ¿un `.toe` de TouchDesigner, una página
de TouchOSC, un grid custom, o algo hecho a medida?

Lo que sí está dicho, y es lo que hay que diseñar:

- Un botón = una acción = un identificador corto y estable. **El identificador es el `S-nn`, el
  `M[tt-vv]` o el `V-nn`**, porque el panel es el sitio donde el operador los ve. La letra
  siempre dice el tipo: `S` efecto, `M` música, `V` vídeo.
- El panel **no puede lanzar el mismo botón dos veces sin que quede claro qué ha pasado**: si
  es un Launch de tipo Gate, tiene que verse encendido. `TODO(preguntar):` cómo se ve en el panel
  que algo está sonando, y cómo se apaga.
- **Un botón para el negro.** Toda la imagen tiene que poder cortarse a negro, igual que todo
  el sonido tiene que poder callarse. Y con el ruido de un proyector detrás, el negro de la
  pantalla tiene que ser **un negro de verdad**, no el gris de la lámpara.
- **El iPad es un punto único de fallo.** Se queda sin batería, se cae, se bloquea. Con el
  panel como única superficie, la obra entera pasa por él. `TODO(preguntar):` un panel
  secundario, o una superficie de reserva que pueda lanzar el sonido sin TouchDesigner.

### Cómo se llama cada pista

> **Corregido el 2026-09-30.** Lo que decía aquí era «el nombre de la pista es el nombre del
> clip», y ya no puede ser: si el identificador va escrito en la pantalla como **nombre del
> clip**, tiene que haber varios clips por pista, y entonces la pista no puede ser un sonido.
> La regla buena es la contraria, y encaja con el panel: **la pista es la familia, el clip es el
> sonido.**

```
LATIDO  (grupo)                  ← el nivel de todos los corazones, uno por pista
├── latido-suyo                  ← cinco pistas, cinco faders, un clip en cada una
├── latido-niño
├── latido-joven
├── latido-parada
└── latido-chica                 ← Launch Mode: Repitch
```

- **Una pista se llama por la familia**, en el sitio donde vive, con sufijo de posición si hace
  falta: `latido-suyo`, `mus-guitar`, `voz-titiritero`. Nombres, no números. Nunca `S-nn` en el
  nombre de una pista: el número identifica un **clip**, y una pista no es un clip.
- **Un clip se llama como el sonido que hace**, y su número va en la libreta de registro, que es
  donde se busca «qué es esto». `latido-06` dentro de la pista `latido-suyo`, y `avivas-03` dentro
  de `mus-guitar`.
- **El panel no enseña nombres de pista.** El operador ve botones, y cada botón lleva el nombre
  del **clip** que lanza. Un botón por clip, no por pista: la pista es un cajón y el botón
  es lo que suena.

**Ningún número se gasta antes de tiempo.** Un `M[tt-vv]` necesita sus dos mitades: `tt` es el
número de pista del disco y se sabe desde el principio, pero **`vv` no existe hasta que esa
variación se construye**, que es después de la puerta `revisada`. **El libreto nunca lleva un
código**: en un borrador se pone el nombre, y del tema solo el **título** si hace falta —
`>> «la voz sola» (del «Avivas el fuego»)`—, que no se puede desincronizar porque es una palabra
y no un número. Los `S-nn` y los `V-nn` igual: sin asignar hasta la puerta, y sin aparecer en el
libreto nunca.

Razón: **el nombre tiene que ser el mismo en el panel, en la pista y en TouchDesigner.** Con el
iPad, el operador no ve esta rejilla, así que el panel es donde el nombre se lee — y el nombre se
lee con el resto de los nombres, en el sitio de siempre.

### Pistas, buses y master — decidido el 2026-09-30

Estaba en `TODO(preguntar)` con una condición: «decidir la arquitectura sin material delante es
inventarla». **Ya hay material delante** — la escena 01 escrita y los stems de «Avivas el fuego»
subidos — así que la condición se cumple y la decisión se puede tomar con criterio.

La idea que la sostiene, y que sale del panel y no de Live:

> **Un bus por familia, un clip por sonido, y los parámetros que el operador tiene que tocar en
> vivo, todos en el panel.** El Set se dimensiona por lo que el operador tiene que poder hacer
> durante la función, no por el número de sonidos que hay.

```
MAIN
│
├── RETORNS
│   └── Dentro            la membrana del estetoscopio + el cuerpo corto
│
├── GRUPOS  (el bus, el nivel, y el ducking)
│   ├── latido            nivel de todos los corazones. SIN devices.
│   ├── musica            nivel de la música. Un compresor, de red de seguridad.
│   ├── voz               el titiritero
│   └── escena            lo que vive de principio a fin: aire, sala, onomatopeyas
│
└── PISTAS
    ├── latido-suyo       midi    → latido-01   Repeat ─┐
    ├── latido-niño       midi    → latido-02   Repeat  │ envío a
    ├── latido-joven      midi    → latido-03   Repeat  │ "Dentro"
    ├── latido-parada     midi    → latido-04   Repeat  │
    └── latido-chica      midi    → latido-05   Repeat ─┘  + Repitch
    │
    ├── mus-guitar        player  → M[01-02] …
    ├── mus-bajo          player  → M[01-02] …
    ├── mus-percusion     player  → M[01-02] …
    ├── mus-palos         player  → M[01-02] …
    └── mus-aire          player  → M[01-02] …       (ROOM L/R, OH, GOLIAT)
```

**Cinco grupos, un Return, y las pistas justas.** No hay pista de efectos, ni canal de Reverb por
defecto: si un efecto necesita un bus propio, se lo crea cuando exista el sonido que lo necesita,
no antes.

#### Por qué un Group y no un Return para la membrana

Porque son dos cosas distintas y confundirlas cuesta:

- **El grupo `latido` es nivel.** Los cinco corazones comparten fader de bus, choke y ducking. No
  lleva devices: si llevara la membrana, los cinco serían filtrados sin excepción, y hay dos que
  no lo son.
- **El Return `Dentro` es timbre.** Es un envío, no un bus: entra lo que le mandes, mezclado con
  lo demás. Va la membrana del estetoscopio y un cuerpo corto.

La ventaja de que sea un envío y no un device del bus es que **el estetoscopio pasa a ser un
knob por pista**. El pitido de la parada y el techno salen con el envío a cero y se oyen en la sala
— que es exactamente lo que dice el libreto: que ahí el aparato miente. Y si un día se decide que
sí suenan filtrados, se suben los envíos: **ninguna de las dos respuestas cuesta nada**, y eso
permite dejar la pregunta abierta sin que bloquee la construcción.

#### Las cinco pistas de latido, y por qué cinco y no una

Porque los cinco corazones **no comparten los mismos parámetros**, y un fader es lo mínimo que
puede ser distinto entre uno y otro:

| Pista | Qué tiene que poder ser distinto |
|---|---|
| `latido-suyo` | el tempo base. Es el que suena en la 11, así que no se toca en directo |
| `latido-niño` | más rápido y más ligero |
| `latido-joven` | «tipo techno, con mucha marcha»: no es un cuerpo, es una máquina |
| `latido-parada` | **el único que no es un latido**: un pitido, y luego el latido vuelve |
| `latido-chica` | el acelerón — `Repitch` a 3/4, manual |

Cinco pistas con la misma rack, pegadas con Ctrl+G y con el mismo ajuste. Suena idéntico a una
sola pista con cinco clips, y en cambio cada corazón tiene su fader, que es lo que hace falta.

#### Los cinco clips laten en bucle, y eso los cambia de arriba abajo

Decidido por el autor el **2026-09-30**: *«cinco clips de latidos, van sonando según el operador,
quedan en bucle hasta que el operador los para»*.

O sea: **`Launch Mode: Repeat` en los cinco, y un botón de parada cada uno.** No son cinco
sonidos que suenan y se acaban — son cinco que **se quedan sonando**. Y eso no es un matiz de
la Launch Mode, es un cambio de cómo se construye cada clip:

**Un clip en bucle tiene que entrar en bucle de verdad.** Y un latido es el peor material que
hay para eso, por lo que hace con la cola:

- El prototipo tenía una **cola de 5 a 7 s** porque era un disparo. En bucle, esa cola **se
  enrolla**: si la cola dura más que el tiempo hasta el siguiente latido, el final de un latido
  se solapa con el principio del siguiente y suena a *flam*, que es exactamente lo contrario de
  un corazón.
- Por tanto **el largo del clip lo fija el tempo**: un número entero de tiempos, y la cola tiene
  que haber terminado antes de que empiece el siguiente. Si el corazón va a 60 lpm, son dos
  tiempos y sobran dos segundos y medio de silencio; eso no es un problema, es lo que hace un
  corazón lento.
- **Un bucle que se oye en bucle tiene que ser aburrido a propósito.** Nada de «lluvia», ni de
  un decaying que se note. Cinco minutos con un latido son cinco minutos, y al tercer minuto el
  público tiene que poder haber dejado de oírlo. **Un sonido en bucle que se vuelve interesante
  es un clip que se va a notar, y se va a notar justo en la 01, que es donde está el fuego.**

Y el bucle arregla una cosa que la escena pedía y no se veía:

> **El bucle es lo que hace que el latido del titiritero pueda *crecer* en la 11.** En el diseño
> viejo el «cuerpo crece» era un problema — un solo latido, tres minutos, y no había forma de que
> pareciera más grande salvo con un filtro y un volumen. Con el clip en bucle, crecer es
> **subir el pitch**: el mismo clip, más rápido, y suena más grande. Un knob, y la pregunta del
> «cuerpo» se responde sola.

**Y el `Repitch` de la chica encaja con el bucle sin tocarse.** `Repitch` sobre un clip en bucle
es el acelerón: el operador sube el pitch fader mientras el corazón se enamora, y el bucle
acelera con él. Es el mismo knob que sirve para el amor y para el cuerpo grande. Verificar en la
máquina el comportamiento exacto de `Repeat` combinado con `Repitch` —que no es lo mismo que
pitchar un clip parado—.

#### La parada tiene que ser un botón, y ahora no puede ser global

Esto contesta el `TODO(preguntar)` que llevaba desde el 27 —«si el panel lleva un botón de parada
por clip, o uno global que corta todo»— y la respuesta es la fácil:

> **Uno por clip. No puede ser global**, y por el bucle esto ya no es una preferencia de
> interfaz. Si el botón global cortara los cinco, en la escena de la parada cardíaca no se podría
> dejar sonando el pitido mientras vuelve el latido del titiritero, que es lo que dice el texto:
> el pitido, la reanimación, **y el latido vuelve**. Y en la 11, si el latido crece mientras
> suena, no se puede apagar el resto.

Con lo cual el panel necesita, como mínimo: **cinco botones de arranque de latido, cinco de
parada, dos faders** (latido y música, para el ducking) **y los botones de cada vídeo.** Se
anota en «El panel», que es donde vive esa lista.

#### El `Repitch` está confirmado

Decidido por el autor el **2026-09-30**, y borra la duda que estaba anotada desde el 29: **se
construye, por la chica**. Motivo 1 (el negro largo de la 11) sigue muerto; el motivo 2 vive. El
corazón de la chica es **un solo clip con `Launch Mode: Repitch`** y el operador acelera mientras
ella se enamora. No se pueden fabricar seis latidos a velocidades distintas porque el acelerón
tiene que seguir la actuación, no el reloj.

#### La mezcla la lleva el operador, no una mesa

Decidido por el autor el **2026-09-30**. Una persona menos en la sala.

La consecuencia técnica es que **`latido` y `musica` tienen que poder bajarse desde el panel, a la
vez, y con dos dedos**. No hace falta un compresor con sidechain —Live no lo tiene nativo—: el
ducking es un movimiento de la mano del operador, que además está donde tiene que estar, que es
al lado de la escena. El compresor del grupo `musica` se queda puesto igual, pero **como red de
seguridad**, no como el mecanismo: para que un latido se cuele un poco sin que nadie se entere.

Y esto contesta la pregunta que estaba abierta desde el 29 —«¿el bus del latido lleva la mezcla, o
la lleva el operador?»— con la respuesta mejor de las dos: **los cinco corazones tienen faders en
el panel**, uno por pista, así que cualquiera de ellos se puede bajar sin tocar el resto.

#### Los stems no son instrumentales sueltos: son una microfonía de sala

Los 75 ficheros de «Avivas el fuego» no son un reguero de pistas mezcladas. Son **la microfonía
completa de una grabación en directo**, y eso cambia cómo se monta la música:

- **Micros de cerca**: `GUIT 440`, `GUIT 441`, `GUIT 8 440`, `GUIT LINE`, `ACU V44 M_`, `BASS DI`,
  `BASS PEDALES`, `DARBOUKA`, `TOM 1/2`, `CAJA PAR`, `SHAKER`, `RIDE`, `SNR`, `HH`.
- **Micros de sala**: `ROOM L 040`, `ROOM R 040`, `ROOM 58`, `GOLIAT 421`, `OH L/R 4038`, `OH L/R
  440`, `Audio 164`.
- **Bombo en cuatro micros**: `KICK 8 640`, `KICK IN e912`, `KICK PAR`, `KICK ROOM`.
- **Voces**: `ALEX`, `IAGO` y `TANIA`, y cada una con `SLAP`, `TF51`, `TF51 DRIVE` y `PLATE`.

Lo que sale de aquí es una decisión de construcción, y es por canción:

> **Montar la música con los micros de cerca, o con los de sala, son dos opciones distintas y
> dan resultados distintos.** Los de sala suenan a la grabación en directo y no se pueden
> arreglar; los de cerca suenan secos y se pueden tratar. Para la 01, «las guitarras, muy limpia y
> suave», son los de cerca — y por eso `mus-aire` no suena en la 01 ni una vez.

`TODO(preguntar):` qué son exactamente los números de los nombres (`440`, `441`, `V44`, `421`,
`4038`, `e912`, `164`, `57`, `8`, `N69`, `69`). **No se inventa.** Casi seguro son referencias de
micrófono o de toma, pero elegir una guitarra «limpia» sin saber si `GUIT 440` es el micro del
amplificador o la entrada de línea es elegir a ciegas. Lo sabe el autor, que estuvo en la
grabación.

#### Lo que el Set NO decide

- **Los números de clip.** Ninguno. `S-nn` se asignan al pasar cada escena por la puerta, y las
  de la 01 no han pasado. Los clips de arriba llevan nombres de trabajo, no números.
- **La cadena de cada sonido.** Lo que hay aquí es la arquitectura: qué buses existen y qué se
  envía a qué. El `Operator` del latido, la membrana y la EQ se construyen con el sonido delante,
  no antes.
- **Si el titiritero es en vivo o una grabación.** El grupo `voz` está para las dos cosas: una
  pista de audio que hoy es una entrada de micro y mañana puede ser una grabación. Que por lo
  visto sea un títere, y eso se decida en `recursos/escena.md`.

### La prueba: la escena 01 contra este Set

Un Set que no se puede usar en la primera escena no es un Set, es un dibujo. Esto es lo que la
escena 01 pide, linea por linea, contra lo que hay arriba:

| Lo que dice el libreto | Qué lo resuelve | ¿Cabe? |
|---|---|---|
| «Se escucha el latido» antes de que entre nadie | `latido-suyo` en bucle, Repeat, con su botón de parada | sí |
| el titiritero aparece por un fade muy suave | un fundido del fader del grupo `latido` | sí |
| «suena de fondo «Avivas el fuego», las guitarras, muy limpia y suave» | `mus-guitar` con `M[01-02]`, micros de cerca, sin `mus-aire` | sí, en cuanto se sepa qué guitarra es la «limpia» |
| «el latido se escucha más vivo y divertido» (niño) | `latido-niño`, distinto tempo y timbre | sí |
| «empieza un latido tipo techno, con mucha marcha» (joven) | `latido-joven` | sí |
| «un pitido como cuando hay una parada cardíaca» y luego el latido vuelve | `latido-parada` y volver a `latido-suyo` | sí |
| «su corazón empieza lento y luego se acelera» (chica) | `latido-chica` con `Repitch` | sí |
| el corazón ha de sonar **dentro de un cuerpo** | el envío a `Dentro` | sí |
| el latido «queda en bucle hasta que el operador lo para» | `Launch Mode: Repeat` y parada por clip | sí, y el clip tiene que estar construido para eso |
| «mientras suena la música de fondo» | `musica` y `latido` bajables a la vez desde el panel | sí |
| el títere habla | grupo `voz` | sí, pero depende de si es en vivo |
| el títere aparece en una pantalla | un clip MIDI que manda OSC a TD, y un `V-nn` | sí, pero **no hay ninguna pista MIDI que mande OSC en este Set** |

**Y aquí aparece el agujero.** La última fila no cabe, y es el único punto que hay que arreglar
antes de desplegar:

> **Falta la pista que habla con TouchDesigner.** El sistema de vídeo está decidido —«8 mm» es
> un proyector disfrazado, Ableton manda OSC y construye la red de TD—, pero en el Set de arriba
> no hay ninguna pista MIDI con un dispositivo que mande OSC, y sin ella ningún vídeo se puede
> disparar desde el panel.

La solución es una sola pista y un dispositivo:

```
td-osc              midi    un clip por V-nn, y un Max for Live que manda el OSC
```

**Es la única dependencia nueva que trae este Set**, y hay que confirmar que hay Max for Live
instalado: sin él, o no hay vídeo desde el panel, o el vídeo se dispara a mano. `TODO(preguntar):`
confirmar M4L en la máquina de la función.

Aparte de eso, la 01 **cabe entera**. Y que quepa la escena que tiene tres latidos distintos, un
acelerón, un pitido, música de fondo y un títere que habla, dice bastante a favor de que el Set no
se queda corto en lo que viene detrás: si el latido solo ya necesita cinco pistas y un bus
propio, la 11, que es el latido con todo un mundo alrededor, va a necesitar menos espacio, no más.

#### Lo que la prueba deja pendiente, y no es del Set

- **Qué guitarra es la «limpia».** Sin eso no hay `M[01-02]`. Es la pregunta de los números de los
  nombres, de arriba.
- **Si el títere habla en vivo o viene grabado.** Cambia el grupo `voz`, no la arquitectura.
- **El nivel de `latido` y de `musica` uno respecto del otro.** Con un iPad en la mano y dos
  dedos, se ajusta en diez segundos con la escena delante. Es una decisión de mezcla, y por
  entonces habrá una oreja al otro lado.

## Un clip es un sonido, no una vez que suena

> **Decidido por el autor el 2026-09-29:** *«Mismo sonido = mismo código, siempre. Si quieres
> otro sonido, es otro código — y merece número, porque es otro sonido.»*

Es la regla que gobierna las tres series, y no tiene excepciones:

- **El mismo sonido que suena en dos escenas es un solo clip.** No uno por escena. El operador
  lo lanza dos veces desde el mismo botón, que es lo que hace de todos modos.
- **Lo que distingue dos sonidos son los ajustes, no la escena donde suenan.** Si el latido de
  la 11 crece, o la variación de la 04 entra con un filtro puesto, eso ya es **otro sonido**, y
  por lo tanto otro clip con su propio número. Que lo merezca no es un gasto: es otro sonido,
  con nombre propio, que se puede buscar.
- **Que un sonido se repita no gasta números.** Dos números para un solo sonido es gasto de
  números, y los números son sagrados.

> **Esto sustituye a la regla anterior**, que decía que un clip era «una ocurrencia concreta» y
> llegaba a poner como ejemplo el latido de la 01 y el de la 11 como dos clips distintos. Ya no.
> El caso era exactamente el de la música —*«el latido no ha cambiado, el mundo sí»*, escribía el
> libreto— y era el ejemplo de la excepción lo que lo hacía raro de verdad. **Sin excepción, no
> hay caso raro.**

El resumen operativo, para cuando haya que decidir: **si dos cosas suenan igual, son el mismo
clip; si suenan distinto, son dos clips y no se discute.**

## La tabla de clips

Una fila por clip — y **una sola fila por sonido**, aunque suene en varias escenas: la columna de
escenas lleva todas las que le tocan. **Los números se reparten por orden de aparición, a medida
que cada escena se cierra** (ver «La numeración», más abajo).

### Los sonidos musicales, que todavía no tienen ni uno

> **Ninguna variación musical está construida, así que ningún `M[tt-vv]` existe todavía.**
> Ni siquiera `M[tt-01]`: el original sin tocar es una convención sobre lo que ocupará el `01`
> cuando haya algo que ocupar, y no un número que se pueda apuntar hoy. Cuando se construya la
> primera variación, esta tabla crece, y **ahí es cuando se empiezan a gastar los `vv`**.

Lo que sí se sabe, por escena, es **de qué tema sale** el material — eso lo decide la escaleta y
no depende de que nada esté construido. Está en [De qué tema sale cada escena](#de-qué-tema-sale-cada-escena).

Cuando haya variaciones, la tabla de esta sección tendrá una fila por variación, con:

| Columna | Qué va |
|---|---|
| **Código** | `M[tt-vv]` |
| **Nombre** | el que va en el panel, en el libreto y en la pista de Live |
| **Tema de origen** | el `tt`, y **solo uno** (regla 4) |
| **De qué está hecha** | qué pistas o instrumentos entran, y qué tratamiento: warp, eco, repetición, MIDI… |
| **Cómo se hace** | el Launch, o el caso de «cadenas de clips» si necesita varias acciones |
| **Escenas** | dónde suena. **Un mismo código puede sonar en varias escenas** |

### Clips que ya están en el libreto

> **Ninguno está asignado, y no se puede llamar así todavía.** Lo que hay es **un clip descrito**
> —el latido, que suena en la 01 y en la 11—, y **ninguna escena ha llegado a `revisada`**.
> Su número **no se conoce**: se asigna al pasar la puerta, en orden de llegada, y como la 11 ya
> no presupone trece clips por delante, hoy no hay forma de saber cuál será. Ver «La numeración».
>
> Por eso este fichero **no usa `S-01` ni `S-14` para hablar de él**: un número escrito antes de
> tiempo es exactamente el error que la puerta viene a cortar. Se llama **«el latido»**, a secas,
> sin número de escena, porque con la regla de «un clip es un sonido» no es de la 01 ni de la 11:
> es de las dos. El `>> [S-nn]` desaparece del libreto (`AGENTS.md`, commit `bc74532`).

| Nombre del clip | Tipo | Escena | Estado | Número | Qué se ve o se oye (texto del libreto) | Material | Cómo se hace en Live / TD | Cómo se lanza | Launch Mode |
|---|---|---|---|---|---|---|---|---|---|
| el latido | `S` | **01 y 11** | `boceto` | **sin asignar** | «un latido. Muy cerca, como si fuera dentro de un cuerpo» — **cinco**, porque el titiritero escucha cinco corazones. **Debajo de la música, con la música entrando casi con la escena**, en las dos | **sin decidir**: el latido sintetizado en MIDI (`latido-prueba`) o el bombo de «Avivas el fuego» | «El latido», abajo | — | — |

> **Una fila, no dos.** El latido de la 01 y el de la 11 suenan igual —mismo archivo, misma
> cadena, mismo ajuste— así que son **un** clip, y se lanza dos veces. Antes eran dos filas con dos
> números, por la regla de la ocurrencia; esa regla ya no existe. La columna de escenas lleva
> `01 y 11` y el número va una sola vez.
| la pantalla de la 01 | `V` | 01 | `boceto` | **sin asignar** | el titiritero aparece desde un fade muy suave en la pantalla del lateral | **sin decidir** | — | — | — |
| los niños proyectados | `V` | 02 | `boceto` | **sin asignar** | niños pintando, amasando, haciendo cosas | **sin decidir**: ¿se filma a niños ahora o son vídeos de archivo? | — | — | — |
| la película que arde | `V` | 02 | `boceto` | **sin asignar** | el proyector echa humo, la cinta se quema, la imagen se degrada y la música se relentece | **sin decidir** — **no hay película**, así que el quemado es un efecto hecho en la red | — | — | — |
| *Alicia* proyectada | `V` | 03 | `boceto` | **sin asignar** | el Sombrerero le dice a Alicia que perdió la muchedad | **sin decidir** — derechos de *Alicia* aparte de los de las voces | — | — | — |
| las siluetas | `V` | 03 | `boceto` | **sin asignar** | salen de la pantalla siluetas de miedo, tristeza y dolor | **sin decidir** | — | — | — |

> **`V` es la tercera serie, y el vídeo va en este mismo fichero** (`AGENTS.md`, commit
> `bac44b6`): *«el vídeo es material tan suena como un efecto […] solo otra columna»*. En el
> libreto va con `>>` y sin número. **Las filas de `V` de arriba son candidatos, no clips:** sin
> material no pasan la puerta, ni con el texto escrito.
>
> Y **`V` hereda de `S` lo que importa:** el número se asigna al pasar la escena por la puerta, y
> no se reutiliza, renumera ni reasigna nunca. Si un vídeo se cae, se marca `caído` y su número
> queda libre para siempre.

> **Nada construido.** `latido-prueba` es un prototipo de prueba, no un clip: no está numerado, no
> está en el Set, y no se ha gastado ningún número. Cuando la 01 pase la puerta se construye
> sobre él o se tira.
>
> **Un clip, no dos.** Antes eran dos, por la regla de que un clip era «una ocurrencia concreta».
> Esa regla ya no existe: el latido de la 01 y el de la 11 suenan igual, y lo dice el propio
> libreto —*«(el mismo latido del principio de la obra. el mismo de verdad)»*—, así que es **un**
> clip lanzado dos veces. Ver «Un clip es un sonido, no una vez que suena».
>
> **Lo único abierto aquí:** si el cuerpo crece en la 11, eso sería un segundo tratamiento y
> habría que construirlo. Ver «El punto que sigue abierto».

### Efectos identificados que todavía no tienen número

Están en la sinopsis o en la escaleta, pero **su escena no tiene texto en el libreto**, así que
no han entrado en la numeración. Cuando su escena pase la puerta, se numeran.

La columna **Material** es la quinta cosa del mensaje (`AGENTS.md`, commit de Datos): **de dónde
sale el material, y si existe.** Las cuatro respuestas posibles son *de la pista*, *existe*,
*hay que conseguirlo* y *hay que fabricarlo* — más *sin decidir*, que es la respuesta que
significa que la puerta **no** se puede dar por buena.

| Escena | Qué se oye | Material | Notas |
|---|---|---|---|
| 02 | — | — | sin efectos propuestos |
| 03 | **un vídeo de *Alicia* proyectado, con el audio del diálogo del Sombrerero y Alicia encima.** Sigue siendo la única escena de la obra sin música del disco | **hay que conseguirlo** — y el material es **doble**: el audio (dos voces, idioma desconocido) **y** la imagen de *Alicia*, que es de Tim Burton | **Ha cambiado de forma.** Antes era solo un audio; ahora el Sombrerero **se ve proyectado**, y además salen de la pantalla **siluetas de miedo, tristeza y dolor** que luego se cargan en la 04. Los derechos de *Alicia* son otra cosa aparte de los de las voces |
| 04 | el tramo de la escena reproducido hacia atrás con efecto de VHS, varias veces | **del tema 04** — «Lo llaman vida» invertido, y hay que elegir el tramo. Al revés no se invierte: se corta una parte y se reproduce invertida | ¿cuántas veces? `TODO` en la escaleta. Y de qué instrumento se saca el tramo, que no está decidido |
| 05 | — | **sin decidir** | la escaleta habla de «formas de discurso vacío» —queja, crítica, juicio— y todavía no está dicho si son imagen o sonido. El libreto no existe |
| 06 | el aviador «da luz con su voz» | **hay que conseguirlo** — otra voz | No estaba en el inventario. La escaleta dice que habla, así que es un audio como el de la 03. **Ver «Una pregunta de material que es de toda la obra»** |
| 07 | el sonido de «salir por donde entraron»; la sinopsis lo llama cisterna | **sin decidir** — si es una cisterna real hay que ir a grabarla; si es una idea, hay que fabricarla | |
| 08 | el ventilador que no deja avanzar la furgoneta | **sin decidir** — la sinopsis dice «un ruido espantoso», así que probablemente hay que fabricarlo | un ventilador real se puede grabar, y suena más real que uno sintético |
| 08 | la furgoneta chocando contra el ojo de la luna | **no hay material: es la ausencia de todos los demás** | En realidad no es un sonido, es un silencio. **Y eso rompe la pregunta por el material.** Ver abajo |
| 09 | barras de colores de señal con su pitido característico | **hay que fabricarlo** | el pitido es del sistema de telecolor, no de la banda. Es un tono de referencia, no un sample |
| 09 | el televisor que vuela con alas | **sin decidir** | |
| 10 | relámpagos y truenos, sin que llueva | **sin decidir** — hay truenos de sobra en cualquier sitio, o se fabrican | la letra dice «Non está chovendo, choverá»: el relámpago y el trueno sin lluvia |
| 12 | — | — | sin efectos propuestos; la escena está vacía |

#### Dos cosas que salen de mirar el material de toda la obra

**1. Las voces no son un problema de la 03, son de la obra.** La 03 tiene un audio de diálogo
entero y la 06 tiene al aviador hablando. Si hay dos voces grabadas, lo lógico es que sean un
**proyecto de grabación solo**: quién las hace, en qué idioma, con qué micrófono, y si comparten
micrófono o timbre. Decide además si los títeres hablan o solo se oye la voz sin boca, que es
una decisión de escena, no de sonido. `TODO(preguntar):` al autor y a Guion.

**2. El silencio no tiene material, y la quinta cosa se queda sin respuesta.** El choque de la
furgoneta contra el ojo de la luna «en realidad no es un sonido: es la ausencia de todos los
demás». Si algún día la puerta exige que el material exista, **un silencio no pasa la puerta**,
porque no hay archivo del que venga. Y sin embargo es un efecto, con su momento, y probablemente
con su clip.

Propuesta: la quinta cosa admite dos respuestas más — **«hay que fabricar silencio»** (bajar todo
el bus de efectos un momento) y **«de dónde no viene»**. Así el silencio es un material más y no
una excepción. Se lo he dicho a Datos; con la regla de los dos mensajes no ha podido recogerlo, así que se lo repito al autor.

### La numeración

**El número se asigna cuando la escena llega a `revisada`.** `AGENTS.md` (commit `86a26f5`).
Ahora mismo **no hay ninguna escena en `revisada`**:

| Escena | Estado |
|---|---|
| 01 El latido | `boceto` |
| 11 El fuego | `boceto` |
| 02-10, 12 | `idea` |

Así que **ninguno de los clips tiene número.** No es que sean provisionales: es que los números
no se conocen. Se asignan al pasar a `revisada`, en orden de llegada.

- **El orden es el de llegada a `revisada`, no el de la obra.** Si la 12 se revisa antes que la
  05, la 12 se lleva los clips bajos y la 05 los altos, aunque en la obra la 05 suene antes. No
  es un error: el número identifica un sonido, no su posición.
- **Un número no se reutiliza, no se renumera y no se reasigna.** Nunca.
- **Una escena que vuelve a `boceto` no mueve los clips que ya tenía.** Si el efecto cambia, el
  viejo se marca `caído`, su número queda libre para siempre, y el nuevo coge el siguiente
  número libre.
- **El `S-nn` solo vive en este fichero** (`AGENTS.md`, commit `bc74532`). En el libreto va el
  nombre del sonido tal como lo oye el público. Así el número no puede desincronizarse: está en
  un sitio.
- **`AGENTS.md` usa `S-01` y `S-14` en su ejemplo del latido.** Como ejemplo está bien, pero
  **los números concretos no se pueden saber hoy**, y un número escrito en un ejemplo es un
  número que la siguiente sesión copia. Y ahora están además **caducados por la regla del sonido**:
  el latido es **un** clip, no dos, así que no puede tener ni `S-01` ni `S-14`. Hay que pedir que el
  ejemplo lo llame «el latido», sin números, y que diga que uno de los dos sería el segundo y el
  otro el séptimo. **Avisado a Datos el 2026-09-29.**

> **El número se escribe en el libreto después de asignarlo, y el libreto es de Guion.** O sea:
> la escena llega a `revisada` → esta sesión asigna el número y lo escribe aquí → Guion lo
> escribe en el `>> [S-nn]` del libreto. Nadie ha escrito esa secuencia. `TODO(preguntar):`
> confirmarla y ponerla en `AGENTS.md`, porque mientras tanto el libreto va a seguir llevando
> números que no existen.

> **Y la puerta habría evitado la colisión del latido.** Todo el lío de «otro tratamiento» /
> «el cuerpo crece» salió de que el libreto llevara un número que nadie había asignado y
> `AGENTS.md` un tratamiento que nadie había decidido. La puerta corta las dos cosas: sin
> `revisada` no hay número, y sin número no hay nada que tratar. `TODO(preguntar):` al autor,
> aunque la recomendación es que no se escriba ningún `[S-nn]` en el libreto hasta que la escena
> pase la puerta.

### El hueco de la puerta: protege el número, no el material

`revisada` congela **el texto**. No dice nada de que el sonido exista. Y como la numeración es
sagrada, eso abre un agujero con dos caras.

**El agujero.** Una escena puede pasar a `revisada` con el texto perfecto y **sin material**. El
clip recibe su número, y ese número **no se puede reutilizar nunca**. Si el efecto después no se
puede construir —porque la grabación no llegó, porque el archivo no existe, porque era una
persona que no vino—, se marca `caído` y el número queda libre para siempre. Se ha gastado un
número en una promesa.

**Ya está pasando, y en la peor escena.** La 03 es un **audio de diálogo entero**: la
conversación entre el Sombrerero y Alicia, con la palabra «muchedad». Ahora mismo no sabemos de
quién son las dos voces, en qué idioma, ni de dónde sale la grabación. Es un material que hay
que **conseguir**, no fabricar. Si la 03 pasara a `revisada` mañana, su clip se numeraría sin
nada detrás.

**Y en el latido, que es más pequeño pero es nuestro.** La 01 está en `boceto` con la fuente
**sin decidir**: ¿el MIDI sintetizado o el bombo de la pista? Si la 01 pasara a `revisada` así,
el clip se numera con la fuente abierta, y el número se gasta en una elección que todavía no está
hecha.

**Tres salidas, y la que recomiendo es la primera:**

1. **El material tiene que existir antes de `revisada`.** La puerta pasa a ser una puerta de
   producción y no solo de escritura: `revisada` significa *el texto está y sé lo que voy a
   construir*. El coste es honesto —algunas escenas se quedan en `boceto` esperando una
   grabación— y el beneficio es que ningún número se gasta en nada.
2. **La puerta no mira el material** y se acepta que un clip numerado pueda ser inconstruible. Es
   legal según la regla, pero es un número en un sobre vacío.
3. **El número es provisional hasta que el material existe.** Rompe «la numeración es sagrada»
   desde el primer día, así que no lo recomiendo.

La (1) se consigue casi gratis: el mensaje de cuatro cosas que ya existe incluye «qué se oye»;
si además incluye **«de dónde sale el material»**, la puerta verifica sola lo que le importa.
`TODO(preguntar):` al autor y a Datos, que es `AGENTS.md` suyo.

### De qué tema sale cada escena

> **La tabla de `P-nn` está retirada.** Los clips `P-nn` identificaban una pista del disco entera,
> y desde el 2026-09-29 la música de la obra no se usa como está. El disco es **material fuente**,
> así que el número de pista ya no identifica lo que suena. Los sonidos musicales llevan
> `M[tt-vv]`, y de cada tema saldrán varios, no uno.

Lo que queda de la tabla antigua es **el reparto de temas por escena**, que no ha cambiado y que
sirve para saber de dónde sale el material de cada una:

| Escena | Tema | `tt` | Fichero | Mezcla |
|---|---|---|---|---|
| 01 | «Avivas el fuego» | **01** | `1_Avivas.wav` | 5:45,3 |
| 02 | «Está bien» | **09** | `9_Está Bien.wav` | 3:23,3 |
| 03 | **sin disco**: audio de diálogo | — | — | — |
| 04 | «Lo llaman vida» | **04** | `4_Lo Llama Vida.wav` | 3:50,0 |
| 05 | «On s'en fout» | **02** | `2_On S'en Fout.wav` | 4:38,4 |
| 06 | «La Reina» | **03** | `3_La Reina.wav` | 5:24,0 |
| 07 | «La puerta» | **06** | `6_La Puerta.wav` | 4:46,0 |
| 08 | «Ser artista» | **05** | `5_Ser Artista.wav` | 3:58,8 |
| 09 | «Vuela» | **08** | `8_Vuela.wav` | 3:33,3 |
| 10 | «Seica» | **07** | `7_Seica.wav` | 4:58,9 |
| 11 | «Avivas el fuego», segunda vez | **01** | `1_Avivas.wav` | 5:45,3 |
| 12 | «Está bien», segunda vez | **09** | `9_Está Bien.wav` | 3:23,3 |

**El prefijo del fichero ES el número de pista del disco.** Confirmado por el autor el
2026-09-29, así que `M[01-01]` es «Avivas el fuego sin tocar» y su material es `1_Avivas.wav`:
**buscar el material de un `tt` y buscar el fichero con ese número es la misma cosa**, y por eso
esta tabla tiene una columna de fichero y no un mapa aparte. Antes el orden venía de una captura
del reproductor y no correspondía con los nombres de los ficheros; `investigacion/referencias.md`
se corrigió ese mismo día.

**Las duraciones son de las mezclas que tenemos, no del disco**, y no son la duración de nada que
suene. Son dos cosas distintas y no se mezclan: el disco es lo que se volcó, el material de
trabajo son estas nueve mezclas, y una variación con ecos o MIDI dura lo que se construya. Lo que
sí dicen es **cuánto material hay**: 5:45 de Avivas es bastante más donde sacar que 3:23 de
«Está bien».

**El disco se abre y se cierra con las mismas dos canciones, en espejo**: la p. 01 abre (01) y
cierra (11); la p. 09 abre (02) y cierra (12). Es la misma forma que el espejo de las escenas
(`guion/escaleta.md`), y es lo que hace que la obra suene a disco y no a lista de reproducción.

## El latido — escenas 01 y 11

El primer sound design de la obra, y el que fija el patrón de todos los demás.

### Lo que dice el libreto

Los dos libretos dicen **lo mismo, con las mismas palabras**:

> `01-el-latido.md`: `>> un latido. Muy cerca, como si fuera dentro de un cuerpo`
> `11-el-fuego.md`: `>> un latido. Muy cerca, como si fuera dentro de un cuerpo`

(En los dos ficheros había además un `>> [S-01]` y un `>> [S-14]` delante. Ya no van: el número
solo existe en este fichero desde el commit `bc74532` de `AGENTS.md`. Y además **los dos números
no tenían sentido**: el latido de la 01 y el de la 11 suenan igual, así que son **un** clip, no
dos. Ver «Un clip es un sonido, no una vez que suena».)

Y en los dos, el latido y la música están **en el mismo sitio del texto** — el latido se anuncia,
y la pista entra justo después:

> `01`: `>> ♪ «Avivas el fuego» (p. 02)` … `**el corazón** (sigue. es el mismo latido que al final de la obra)`
> `11`: `>> ♪ «Avivas el fuego» (p. 02)` … `(el mismo latido. es el mismo corazón del principio de la obra)`

Las dos escenas tienen la misma forma: **el latido solo, un rato, y luego la música entra.** Lo
que cambia entre la 01 y la 11 no es el sonido: es todo lo que hay alrededor (el propio libreto
lo dice: «el latido no ha cambiado, el mundo sí»). Por eso el clip de la 11 es el mismo sonido con el
mismo tratamiento, y no una versión nueva.

> El «(sigue)» del 01 se leía antes como que el latido **seguía por encima de la canción**. Ya
> está resuelto: no. Ver «Lo que está decidido».

### DECIDIDO, Y LUEGO CAMBIADO — leer esto antes que nada de abajo

> ⚠️ **Todo lo que sigue en esta sección se escribió sobre una decisión que el autor ha
> cambiado después.** Se conserva por trazabilidad, y porque explica el camino, pero **el
> diseño actual es el del bloque siguiente.**

La versión anterior venía de una respuesta de Guion en `11-el-fuego.md`:

> «el latido se oye solo en el silencio de antes, y desde que entra la pista ya no hay nada que
> recortar — es la misma pista en las dos escenas.»

De ahí salió «el latido no suena encima de la música: suena antes, y la pista lo sustituye», la
idea de que el «(sigue)» del libreto significaba que el latido se había convertido en la
canción, y la decisión de **no construir el `Repitch`** porque el negro era corto.

**El autor lo ha precisado** (2026-09-28, confirmado por Guion el mismo día):

> **«El latido va debajo de la música en las dos escenas del espejo, con la misma cadena y el
> mismo ajuste»**, y **no hay negro largo: la pista entra casi con la escena**, en «un corazón»,
> muy suave y de fondo.

Y lo ha dicho después de reescribir la escena 01, que es donde está la explicación. Ver «El
silencio largo: no existe».

## El vídeo — en el mismo fichero, y por qué

> **Decidido por el autor (2026-09-28):** *«vamos a usar `sonido.md` para sonido y video, le
> podemos llamar `audiovideo.md`»*. Escrito en `AGENTS.md` (commit `bac44b6`) y aplicado a las
> quince referencias. **El fichero se llama `recursos/audiovideo.md` y este texto es el que
> sigue.** **No se crea `recursos/video.md`.**

Mi propuesta de antes —partir en `imagen.md` y `panel.md`— **queda anulada.** La escribí apoyándome
en la regla de los tres niveles, que decía que este fichero no podía llevar imagen. El autor ha
decidido lo contrario, y el motivo que él da es mejor que el mío: *«hay un solo operador
disparando desde una sola mesa: partir la lista en dos se nota justo en el momento en que hay que
clavar un vídeo y un sonido a la vez»*. Es exactamente el problema que resolvería tenerlos juntos.

**Lo que sí cambia por renombrar:** antes «sonido» y «vídeo» eran cosas distintas hasta en el
nombre. Ahora el fichero tiene que **distinguir por sección y por serie**, porque todo lo demás es
compartido: mismo panel, misma puerta, mismo operador, mismo momento.

### `V-nn` no es un clip: es un parameter de TouchDesigner

> **Decidido por el autor el 2026-09-30**, al pasar la documentación al vocabulario de Live y
> TouchDesigner: Live **no tiene clips de vídeo**, y decir que sí los tiene es mentira. Un vídeo
> es una red CHOP y lo que se pulsa es un **parameter** de TouchDesigner.

Esto obliga a separar lo que hasta aquí venía mezclado. Cuando el operador «lanza un `V-nn`» pasa
a ser exactamente esto:

| Pieza | Dónde vive | Qué es |
|---|---|---|
| **El número `V-nn`** | nombre del **parameter** en TouchDesigner, y `audiovideo.md` | el identificador del vídeo |
| **El vídeo** | una red **CHOP** dentro del component: Movie In → Transform → Composite → Movie Out | la imagen |
| **Lo que lo dispara** | un **clip MIDI** de Live en una Launch track, que manda el **OSC** | el botón |

**El clip MIDI es un `S-nn` como cualquier otro**, y su número es propio. Un vídeo, entonces,
**no es una serie aparte con su propio número**: es un parameter (`V-nn`) más un clip que lo
enciende. El `V-nn` identifica **el vídeo**, que es lo que se numera; el clip que lo dispara lleva
un `S-nn` como cualquier otro disparo de la obra.

**Esto no contradice la regla de que el número no se reutiliza nunca.** Un vídeo que se cae deja
su `V-nn` libre para siempre, igual que un efecto, y su clip sigue ahí, muerto y sin usar. Pero
**no es lo mismo**: el `V-nn` está en TouchDesigner y el `S-nn` en la Session View, y eso hay que
saberlo antes de buscar un número.

Lo que **sí** se conserva de la regla que se escribió antes:

- El material de un vídeo puede no existir, y eso bloquea igual que en un efecto: la 02 y la 03
  no tienen de dónde sacar la imagen ni la voz, así que no pasan la puerta ni con el texto
  escrito.
- En el libreto, el vídeo va **con `>>` y sin número**, igual que el resto: `>> un vídeo de niños
  proyectados`. Y `**` queda para la luz.

### El sistema de vídeo, tal como está decidido

> `AGENTS.md` (commit `bac44b6`), por decisión del autor:
>
> - **El 8 mm es un proyector de vídeo normal disfrazado. No hay película de verdad.**
> - Los vídeos van **de Live a TouchDesigner por OSC o MIDI**.
> - **La red de TouchDesigner la construye esta sesión**: el aspecto de 8 mm, el quemado y el humo.
> - El incendio es **humo más un efecto de vídeo quemándose**.

Lo que esto significa para aquí, y son las cuatro cosas que hay que decidir antes de construir:

1. **OSC, no MIDI.** Como está escrito «por OSC o MIDI» y hay que elegir: **lo que va dentro de
   una pista larga necesita la posición**, y MIDI no la lleva. Ver «cadenas de clips».
2. **La dirección.** Está escrito «de Live a TouchDesigner». Con el panel del iPad como
   superficie, la topología natural es la contraria —el iPad habla con TouchDesigner, que es el
   programa que está hecho para recibir y repartir control, y TouchDesigner manda MIDI a Live— y
   además es la que permite que TD sepa dónde va la pista. Pero el autor ha escrito lo otro, así
   que **es de él, no mía**: `TODO(preguntar)`.
3. **Un botón puede lanzar de las dos máquinas.** «Indefinidamente o conjuntamente» del panel.
   Ver «cadenas de clips».
4. **El negro tiene que ser un negro de verdad.** Si el incendio es humo, el humo tapa la
   proyección y detrás hay un proyector encendido: el apagado no es «dejar de enviar vídeo», es
   bajar la lámpara. `TODO(preguntar):` qué hace el botón de negro.

### El panel

Está aquí, en este fichero, **no en otro.** Es la pieza que ve a las dos máquinas, y con el autor
decidiendo que las dos cosas viven en el mismo fichero, el panel se documenta aquí también. La
tabla del panel tiene que tener **una columna que diga si el botón golpea en Live, en TD, o en
las dos** — que es la que hace que la sincronía no sea un problema.

`TODO(preguntar):` qué es exactamente el panel. ¿Un `.toe` de TouchDesigner, TouchOSC, un grid
hecho a medida? Y cómo se ve en el panel que algo está sonando, y cómo se apaga, si el operador ya
no ve la Session View.

## Aparcado: la escena 11

> **Decidido por el autor (2026-09-28): la 11 se trabaja más adelante.** No se toca, y todo lo
> que aquí estaba sobre ella queda pendiente de reordenarse cuando llegue el momento. Se anota
> para que no se pierda, no para trabajarlo.
>
> **Lo que ya está decidido de la 11 no hay que volver a decidirlo**, porque el espejo lo ata a
> la 01 y la 01 avanza:
>
> - **El latido va debajo de la música, con la misma cadena y el mismo ajuste que el de la 01, y
>   la pista entra casi con la escena.** No hay negro largo. El autor lo ha cerrado y ha añadido
>   el motivo: con la pista debajo desde el principio, cambiarle el timbre se oye mucho menos, lo
>   que hace el trabajo es lo que pasa alrededor. Ver «El silencio largo: no existe».
> - **La 11 deja de ser el caso raro.** No hace falta un segundo tratamiento del latido.
> - **El espejo de forma la escribió Guion y es la buena:** «el mundo se **monta** alrededor del
>   corazón aquí, y en la 11 ya está montado». Un espejo en el tiempo, no en el contenido.
> - **Lo único que queda, y es mío:** cuál de los cinco corazones de la 01 es el de la 11.
>   Propuesta de Ableton: el primero, el del titiritero consigo mismo. Ver «El espejo 01 ↔ 11».
> - La 11 lleva también el 8 mm quemándose, el humo y el árbol que brota: es decir, todo lo que
>   se acaba de decidir para el vídeo entra aquí. Eso la convierte en la escena más cara de la
>   obra, y es una razón más para dejarla para después.

## El latido — el diseño actual

Todo lo que viene a partir de aquí es lo que hay que construir. Lo anterior queda como historia.

### Ya no es un latido: son cinco

El autor ha reescrito la escena 01 (`01-el-corazon.md`, `boceto`, texto del autor). Y el latido
ya no es un sonido solo, sino **cinco versiones** — el propio `TODO` de Guion en la escena
los cuenta: «cinco versiones del latido».

| # | A quién escucha el titiritero | Qué es | Qué implica |
|---|---|---|---|
| 1 | él mismo, con el estetoscopio, antes de salir | un corazón normal, **dentro de un cuerpo** | el que abre la obra y el que se supone que suena en la 11 |
| 2 | un niño | «más vivo y divertido» | más rápido, más ligero |
| 3 | un joven | «tipo techno, con mucha marcha» | **ya no es un cuerpo: es una máquina** |
| 4 | alguien a quien se le para | pitido de parada cardíaca al segundo compás, reanimación, y el latido vuelve | el único que **no** es un latido |
| 5 | una chica de la que se enamora | «empieza lento y luego se acelera» | **una aceleración dentro del sonido** |

### El estetoscopio es un filtro, y eso unifica las cinco versiones

Esta es la idea más útil que trae la reescritura, y es técnica. La escena dice:

> «el aparato es la explicación visible de que el latido suena **dentro de un cuerpo**, que es lo
> que dice la implementación en `recursos/sonido.md`»
>
> (Cita literal del libreto. El nombre del fichero ya no es ese: ahora es `audiovideo.md`. La cita
> no se cambia porque es lo que dice la escena, pero el enlace que tiene detrás está roto, y el
> `01-el-corazon.md` es de Guion.)

Es decir: el **latido suena a través del estetoscopio**, no a pelo. Y un estetoscopio real tiene
una membrana en la campana que **se come los agudos y deja el «lub-dub»**: por eso un corazón de
verdad,junto a un estetoscopio, suena así y no como un bombo.

Si el latido se filtra por esa membrana, entonces:

- **un solo sonido de latido** puede dar las cinco versiones sin dejar de ser el mismo latido, y
  la diferencia entre un niño y un joven es el **material que entra** filtrado, no cinco
  efectos distintos. Eso hace que «el mismo latido que en la 11» siga siendo verdad con cinco
  versiones encima.
- El techno y la parada cardíaca **no son latidos filtrados**: son otra cosa. Y está bien que lo
  sean. El techno es el corazón que se ha convertido en máquina, que es lo que dice el texto; el
  pitido es la parada. **El estetoscopio miente en esos dos momentos, y a propósito.**

> `TODO(preguntar):` ¿el pitido de la parada cardíaca se oye **por el estetoscopio** o por la sala?
> En realidad, por un estetoscopio no se oye una parada: se oye silencio. Así que el pitido es un
> recurso narrativo y decide si la escena se lo cuenta al público o no. Es dramaturgia, no
> mezcla.

### `Repitch`: sigue haciendo falta, pero por la chica

> **Guion dice que no lo construya.** Y tiene razón sobre el motivo que él da —el negro largo—, que
> ya no existe. **Pero el motivo no era el único, y el segundo sigue vivo.** Si se quita el
> `Repitch` sin mirar esto, la escena 01 no se puede construir.

El `Repitch` se pidió **dos veces**, por dos razones distintas, y conviene no mezclarlas:

| | Por qué se pidió | Estado |
|---|---|---|
| **1. El negro largo de la 11** | tres minutos de un golpe repetido clavado son un metrónomo, no un corazón | **MUERTO.** No hay negro largo: la pista entra casi con la escena |
| **2. La chica de la 01** | su corazón «empieza lento y luego se acelera»: una rampa de velocidad **dentro del mismo clip** | **VIVO.** Está en `01-el-corazon.md`, y esa escena no se cae |

La razón 2 no dependía del silencio. Depende de una línea del texto del autor:

> *«va a junto de un chica y su carazón empieza lento y luego se acelera... el titiritero se hace
> el canchero ya que ella se enamoró»*

Con `Launch Mode: Repitch` eso es **un solo mando**: el operador acelera el corazón mientras la
chica se enamora, sin disparar clips ni automatizar a mano. **Sin `Repitch` habría que fabricar
cinco o seis clips de latido a velocidades distintas y encadenarlos**, que es exactamente el
trabajo que la herramienta evita — y que además no sale igual delante del público, porque el
acelerón tiene que seguir a la actuación, no al reloj.

> `TODO(preguntar):` confirmar que la 2 sigue viva. Guion ha cerrado su turno de dos mensajes
> («no lo construyas»), así que la pregunta va al autor, que es quien escribió la línea. **No
> construir el `Repitch` por la razón 1; por la razón 2 sí, y antes de construir el latido.**

> Y un detalle de la misma línea: **«se enamora» es del titiritero, no de ella.** La chica no
> acelera el corazón porque se enamore, sino porque el titiritero se enamora al oírla. El
> acelerón es **una actuación**, no un estado. Eso refuerza que el latido tiene que ser
> manipulable en vivo y no una grabación cerrada.

### El espejo 01 ↔ 11, cerrado salvo una cosa

El espejo ya no es «el mismo latido, dos veces». La 01 tiene cinco corazones y la 11 tiene uno.
Lo dice la nota de la escena:

> «el mundo se **monta** alrededor del corazón aquí, y en la 11 ya está montado»

**El espejo se ha movido:** aquí se monta el mundo alrededor del corazón, y allí ya está montado.
Eso es un espejo en el tiempo, y es mejor que el de antes. Y **el autor ha cerrado lo demás**:
mismo archivo, misma cadena, mismo ajuste, **un solo clip en las dos escenas**, y el 11 deja de
ser el caso raro: deja de ser un caso.

**Lo único que queda, y es mío y no de Guion:** la 01 tiene cinco corazones y el 11 tiene uno,
así que «mismo archivo» solo puede referirse a uno de ellos. **¿Cuál de los cinco es el de la 11?**
Propuesta de Ableton, y sigue siendo la misma: **el primero, el del titiritero consigo mismo.** Es
el que suena antes de que él entre en la 01, así que cuando aparece ya estamos oyendo su
corazón, y en la 11 ese mismo corazón está solo con todo lo demás alrededor. Si fuera otro, el
espejo se rompe en el único punto donde el público está mirando. `TODO(preguntar):` decide el
autor.

### Dos cosas técnicas que vuelven

**1. El `Repitch`** está en la sección de arriba, con sus dos motivos separados. Se construye por
la chica, no por el silencio.

**2. Al ir debajo de la música, el latido necesita nivel propio y poder callarse.** `AGENTS.md`:
*«cada clip necesita poder callarse»*. Un latido que suena la escena entera con la música debajo no es un
latido: es una capa, y una capa que compite. Consecuencias:

- **Los cinco clips necesitan faders separados** del bus del latido, no uno.
- **Alguien tiene que poder bajarlos sin que el operador se entere.** Si el latido tapa la
  guitarra, la mezcla la tiene que corregir una persona, no la tiene que corregir el titiritero
  en escena. `TODO(preguntar):` ¿el bus del latido lleva la mezcla —y entonces hay una mesa
  delante—, o lo lleva el operador en su panel?
- **El bus del latido necesita ducking**, porque hay momentos en que la música manda: el
  relentecimiento de la 02, la salida de «Avivas el fuego» hacia «Está bien».
- **Y el nivel es una decisión de mezcla, no de sonido.** Ver ««Debajo de la música» es una palabra
  de la ficción».

### Qué cambia con esto

**El latido sintetizado en MIDI pasa a ser la opción correcta.** Se descartó cuando parecía que
iba a tener que sonar seis minutos y medio por encima de «Avivas el fuego», compitiendo con
ella. No es el caso: solo tiene que soar en el negro, solo, antes de la pista. Y en esa
condición es un sonido expuesto —nada lo tapa— así que **la cola de reverberación se oye
entera**. Por eso el «cuerpo, no caverna» pasa de ser una corrección de gusto a ser
obligatorio: de 28 s a 5-7 s.

**Cuánto dura el latido se decide con la variación, no con la escena.** Cuando la variación
musical esté construida —su `vv` asignado—, se verá si el relevo pide dos sonidos o uno. Antes
de eso es una pregunta sin respuesta: **no se puede clavar un relevo contra un original que
está sonando**, porque el material de la 11 se va a reescribir.

**El relevo del latido a la pista es la única parte técnica de verdad.** Un clip se para y otro
empieza, y entre los dos hay un momento. `TODO(preguntar):` cómo se hace el relevo.

### El silencio largo: no existe

> **Decidido por el autor (2026-09-28), confirmado por Guion:** el latido va **debajo de la
> música en las dos escenas del espejo, con la misma cadena y el mismo ajuste** — también en la
> 11. **Y no hay negro largo: la pista entra casi con la escena**, en «un corazón», muy suave y
> de fondo. El fondo entero va con la variación musical debajo.
>
> Con esto se cierra también la pregunta de si el cuerpo crecía en la 11: **con la pista debajo
> desde el principio, cambiarle el timbre al latido se oye mucho menos, no más.** Lo que hace el
> trabajo es lo que pasa alrededor, no el sonido. Mismo archivo, misma cadena, mismo ajuste,
> **un solo clip**. **La 11 deja de ser el caso raro** y las dos escenas se construyen
> exactamente igual.

Desaparecen con esto dos cosas que estaban pendientes: el negro largo, y la posibilidad de que
la 11 pidiera un segundo tratamiento. También se cae el `TODO` de **«el fondo de sala debajo del
latido»**: ese «algo debajo» es ahora la canción, y la pregunta está contestada sola.

Y **la cola deja de ser crítica.** El argumento era que el latido sonaba solo y desnudo, y que
por eso la cola de 28 s del prototipo se oía entera. Con la música debajo la cola está tapada, así
que **5-7 s sigue siendo lo correcto** —porque el libreto dice *cuerpo, no catedral*— pero ya no
decide nada. Anotado para no seguir cargando la decisión sobre ella.

> **`«Debajo de la música» es una palabra de la ficción, no del fader.** Este es el punto técnico
> del cambio, y conviene dejarlo escrito antes de construir: un latido de 130 Hz **por debajo**
> de una pista de guitarras de la obra, en un nivel que cuente como «debajo», **no se oye en una
> PA**. Así que el bus del latido va, en la mezcla, **por encima de los graves de la pista**, o
> tiene su propio espacio. El latido está debajo en el relato y el que manda en la mezcla es la canción.
>
> `TODO(preguntar):` el nivel exacto que tiene que tener el latido sobre la pista es una
> decisión de mezcla con el autor delante, no se decide aquí.

### El punto que sigue abierto: ¿el cuerpo crece en la 11?

La pregunta es real y sigue viva. `11-el-fuego.md` la plantea bien y bien atribuida: el latido
se oye solo en el negro, y en la 11 ese mismo latido tiene delante un paisaje. ¿Basta con eso, o
el sonido **cambia** —cola larga, exterior, distancia, haciéndose paisaje?

| | El sonido no cambia | El cuerpo crece |
|---|---|---|
| Qué hace | **un** clip, idéntico en las dos escenas | otro clip para el 11: la misma fuente con la cola más larga |
| Qué dice la escena | «el latido no ha cambiado, el mundo sí» | el cuerpo se hace paisaje |
| Riesgo | el final podría sonar repetido si el público no ve el cambio | el espejo se rompe en lo que la obra dice que no se rompe |

Mi recomendación sigue siendo la primera, y ahora con un argumento más: la propia escena 11
tiene ya escrito `(el latido se ha convertido en la canción. ya no se oye aparte: es la música)`.
Si además el latido *suena* distinto en la 11, ese texto miente, porque no se ha convertido en
la canción: sigue siendo un sonido. Con el mismo sonido en las dos escenas, la frase es
exactamente cierta. `TODO(preguntar):` decide el autor.

### Propuestas (no son decisiones)

- ~~**El fondo de sala debajo del latido**~~ — **cerrado, y solo con el negro.** Ese «algo
  debajo» era para cuando la escena se quedaba en negro y un latido, porque el silencio
  absoluto de la sala suena a avería. **Ya no hay negro largo, así que la canción es lo que
  está debajo** y la pregunta se contesta sola. Si la 01 termina con un negro otra vez, vuelve a
  ser una pregunta.
- **Tres golpes distintos en vez de uno en bucle**, en filas separadas. El argumento ya no es
  que el silencio suene poco: es que **con la música debajo, un golpe idéntico cada 0,46 s se
  vuelve un metrónomo en la mezcla**. Tres golpes en vez de uno lo hacen mejor y más barato:
  tres clips, tres sonidos, tres filas.

## El flujo de trabajo del canal

### La puerta: `revisada`

Hasta que una escena no está en `revisada` en `guion/escaleta.md`, **no se trabaja su sonido**.
Con la escena en `idea` o `boceto`, Guion sigue nombrando el sonido en el libreto, pero eso no
es un encargo. El estado no se da por supuesto: se comprueba.

```bash
grep "| 12 |" guion/escaleta.md
```

Si llega una propuesta de una escena que no está en `revisada`, se dice y no se trabaja: **no es
de esta sesión decidir que un texto ya está.** Y si falta algo para construir un efecto, se
pregunta a Guion; no se deduce.

### Lo que tiene que traer un mensaje

Cinco cosas. Si falta una, no se puede empezar:

1. **Qué escena y en qué estado.** «Escena 12, `revisada` esta tarde».
2. **Qué se necesita.** El efecto o la pista, con su nombre tal como lo escribió Guion.
3. **Dónde y cuándo.** En qué punto de la escena, y en qué momento.
4. **Por qué en ese momento.** Qué le pasa a la escena, a la imagen o al público justo ahí.
5. **De dónde sale el material.** Archivo, pista del disco, grabación que hay que conseguir, o
   algo que hay que fabricar. **Si la respuesta es «todavía no lo sé», el material no está
   resuelto y la puerta no se puede dar por buena**: eso se pregunta antes, aquí, o en el hilo de
   Guion. Añadido por Datos; en vigor desde ya.

> **La quinta cosa tiene dos huecos, y los dos son reales.** La escena 08 pide un efecto que
> **no es un sonido sino la ausencia de todos los demás** — el choque contra el ojo de la luna.
> Y una escena puede necesitar un sonido del que todavía **no sabemos ni el nombre**. Las dos
> cosas tienen respuesta, pero tienen que estar escrito: «hay que fabricar silencio» y «de dónde
> no viene». Ver «Dos cosas que salen de mirar el material».

**Y una cosa que NO está decidido:** si el material tiene que existir **antes** de la puerta. El
autor ha dicho que todavía no, y que lo quiere ver con las escenas 03 y la 01 delante. Así que de
momento **la puerta es solo sobre el texto** y la quinta cosa es la que avisa. Cuando se decida,
se escribe aquí. `TODO(preguntar):` pendiente del autor.

**Y la consecuencia de «verlo con la 03 delante»:** la pregunta no se puede decidir antes de que
la 03 tenga texto, porque la 03 *es* el caso. El diálogo entre el Sombrerero y Alicia está ahora
en el camino crítico de una decisión de protocolo, no solo de su propia escena.

### Qué hace esta sesión cuando el mensaje está bien

1. **Qué se oye** — una frase dramática. Es lo primero, porque es lo que va al libreto. Si no se
   puede decir en una frase, todavía no se sabe qué efecto es.
2. **De dónde sale el material** — una grabación real, un sample de campo, un sintetizador, o
   un fragmento del disco. Si no está resuelto: `TODO(preguntar):`, y se pregunta al autor.
3. **El número**, si la escena acaba de pasar la puerta. Se asigna aquí y se escribe aquí; en el
   libreto lo escribe Guion.
4. **Cómo se hace en Live** — pista, efecto, automatización, Launch Mode, forma de parar. Esto
   se escribe con Ableton delante, no de memoria.

Los pasos 1, 3 y 4 son de este canal. El 2 necesita material.

## TODO(preguntar)

**Al autor, por orden de lo que bloquea:**

- **¿La puerta exige que el material exista?** `revisada` congela el texto pero no el sonido, y
  como el número no se reutiliza nunca, una escena puede pasar la puerta sin material y gastar
  un clip en nada. Ya pasa en la 03 (audio de diálogo, nadie sabe de quién son las voces) y en la
  01 (la fuente del latido está sin decidir). Recomiendo que el material exista antes de la
  puerta. Ver «El hueco de la puerta».
- ~~**¿El cuerpo crece en la 11?**~~ **Contestada: no.** Con la pista debajo desde el principio,
  cambiarle el timbre se oye mucho menos, no más. Mismo archivo, misma cadena, mismo ajuste, **un
  solo clip** en las dos escenas. Ver «El silencio largo: no existe».
- ~~**¿Negro corto en las dos escenas?**~~ **Contestada: no hay negro largo.** La pista entra
  casi con la escena, en «un corazón», muy suave y de fondo. Ver «El silencio largo: no existe».
- **¿El `Repitch` se construye?** Guion dice que no, y por su motivo es verdad, pero por el
  motivo de la chica es necesario. Es la pregunta abierta más urgente de esta lista. Ver «
  `Repitch`: sigue haciendo falta, pero por la chica».
- **¿Cuál de los cinco corazones es el de la 11?** Propuesta de Ableton: el primero, el del
  titiritero consigo mismo. Ver «El espejo 01 ↔ 11, cerrado salvo una cosa».
- **¿El nivel del latido sobre la pista?** «Debajo» es una palabra de la ficción; en la mezcla
  tiene que ir por encima de los graves de la pista o no se oye. Ver ««Debajo de la música» es
  una palabra de la ficción».
- **¿El árbol brota en un momento concreto de «Avivas el fuego»?** Si la imagen va clavada a un
  compás hay que conocer la pista por dentro; si se mueve libre sobre ella, el operador lanza y
  la imagen sigue. Pregunta para Guion. Ver «El silencio largo: no existe».
- **El relevo del latido a la música.** Ya no es un relevo sino una mezcla larga: no hay un
  momento de relevo, hay una relación de niveles constante. Ver arriba.
- **El material: ¿el latido sintetizado o el bombo de la pista?** El sintetizado
  (`latido-prueba`) ya existe y es la opción correcta desde que el latido suena solo. Con el
  bombo de la pista el relevo sería limpio, pero el sonido sería menos «dentro de un cuerpo».
- **La cola: 5-7 s, no 28.** El prototipo del MCP tenía 28 s, que es «en una catedral», y el
  libreto dice «dentro de un cuerpo». Ahora además el latido suena sin nada encima, así que la
  cola se oye entera. **Cuerpo cerrado y cercano, no espacio grande.**
- **Con qué PA se representa.** Decide el material entero: un latido por debajo de 80 Hz no se
  oye, y con eso se decide la zona del sonido.
- **El fondo de sala debajo del latido.** Decidido antes de que la escena 01 se quedara en
  negro, y ahora «negro y un latido» puede ser incompatible con «algo debajo».

**A las otras sesiones:**

- **La escena 03 es la única sin música, y ahora es doble: vídeo y audio.** El Sombrerero **se
  ve proyectado** y el audio es el diálogo de *Alicia*. `TODO(preguntar):` de quién son las dos
  voces, en qué idioma, de dónde sale la grabación, **de dónde sale el vídeo de *Alicia***, y si
  el Sombrerero proyectado sale de la película o hay que fabricarlo. Los derechos van a `Datos`.
- **La numeración S-nn.** Cambiada por la puerta de `revisada` (commit `86a26f5`): el número se
  asigna cuando la escena llega a `revisada`, en orden de llegada y no de obra, y no se
  reutiliza ni se renumera nunca. `TODO(preguntar):` la secuencia de escritura del número, que
  va de esta sesión a `audiovideo.md` a Guion y de ahí al libreto, y que no está en `AGENTS.md`.
- **El eco.** Si la sala tiene reverberación, ¿el disco entra por el PA directamente o pasa por
  Live? Afecta a toda la arquitectura, y en la 01 y la 11 más que en ningún otro sitio: son
  escenas con mucho silencio.
- ~~**El Set no existe todavía.**~~ **Resuelto el 2026-09-30**: la arquitectura está decidida y
  está en «Pistas, buses y master», con la prueba de que la escena 01 cabe entera. **Lo que no
  existe es el Set construido**, y hay un hueco: **falta la pista `td-osc`**, la única que habla
  con TouchDesigner, y depende de que haya Max for Live. La superficie de control ya estaba
  decidida desde el 28: el panel de OSC en el iPad.
- **Qué material hay grabado.** No hay inventario. ¿Qué sounds, qué field recordings, qué hay en
  el móvil de alguien?
