# Sonido

> **Todo el sonido de la obra, en Ableton Live.** La música del disco, los efectos sonoros y
> la parte técnica. Un solo fichero porque hay un solo Set, un solo operador y un solo
> interruptor.
>
> **Doce escenas** en tres actos, con la música colocada y el disco cerrando donde abre
> (`guion/escaleta.md`).
>
> **Estado: convención decidida. Set sin construir.** Está escrita la forma de trabajar —qué es
> un cue, cómo se numera, cómo se dispara— y hay dos cues **descritos pero sin número** (el
> latido de las escenas 01 y 11) y el resto de los efectos inventariados pero sin número. No hay
> una sola pista de Live construida, salvo el prototipo `latido-prueba` que se pidió al modelo
> del MCP para probar el carácter del sonido.
>
> La convención de marcado vive en `AGENTS.md`, sección «El sonido». Este fichero es su
> ejecución: la tabla de cues y las decisiones técnicas.
>
> **Reparto:** este fichero es de la sesión de Ableton. Lo nombra Guion y lo decide aquí; lo
> anota Datos.

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
latido-01            audio       → (nº al pasar la 01 por la puerta)
relampagos-10         audio       → (nº al pasar la 10 por la puerta)
caja-vacio            audio       → (nº al pasar la 07 por la puerta)
p-02-avivas-el-fuego  audio       → P-02
```

Los `P-nn` sí llevan su número desde el primer día. Los `S-nn` no: se escriben aquí al pasar la
escena por la puerta, y en un borrador como este se pone entre paréntesis para no gastar un
número que todavía no existe.

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

Una fila por cue. **Los números se reparten por orden de aparición, a medida que cada escena
se cierra** (ver «La numeración», más abajo).

### Cues que ya están en el libreto

> **Ninguno está asignado, y no se puede llamar así todavía.** Lo que hay son **dos cues
> descritos** —el de la escena 01 y el de la 11—, y **ninguna escena ha llegado a `revisada`**.
> Sus números **no se conocen**: se asignan al pasar la puerta, en orden de llegada, y como la
> 11 ya no presupone trece cues por delante, hoy no hay ni forma de saber cuáles serán. Ver «La
> numeración».
>
> Por eso este fichero **no usa `S-01` ni `S-14` para hablar de ellos**: un número escrito antes
> de tiempo es exactamente el error que la puerta viene a cortar. Se llaman «el cue de la 01» y
> «el cue de la 11», y el `>> [S-nn]` desaparece del libreto (`AGENTS.md`, commit `bc74532`).

| Cue | Escena | Estado | Número | Qué se oye (texto del libreto) | Fuente | Cómo en Live | Disparo | Parada |
|---|---|---|---|---|---|---|---|---|
| el de la 01 | 01 | `boceto` | **sin asignar** | «un latido. Muy cerca, como si fuera dentro de un cuerpo» — **solo en el negro, antes de que entre la pista**, dos o tres golpes | **sin decidir**: el latido sintetizado en MIDI (`latido-prueba`) o el bombo de «Avivas el fuego» | «El latido», abajo | — | — |
| el de la 11 | 11 | `boceto` | **sin asignar** | «un latido. Muy cerca, como si fuera dentro de un cuerpo» — **el mismo archivo, misma cadena y mismo ajuste que el de la 01**. Mismo negro corto: entra la pista casi igual que en la 01 | la misma que el de la 01 | «El latido», abajo | — | — |

> **Nada construido.** `latido-prueba` es un prototipo de prueba, no un cue: no está numerado, no
> está en el Set, y no se ha gastado ningún número. Cuando la 01 pase la puerta se construye
> sobre él o se tira.
>
> Dos cues porque son **dos ocurrencias del mismo sonido en dos escenas**, no dos sonidos. Lo
> escribe el libreto: *«(el mismo latido del principio de la obra. el mismo de verdad)»*. La
> numeración está confirmada en `AGENTS.md` y en `11-el-fuego.md` (commit `5bc4d86`).
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
| 03 | **un audio de diálogo**: la conversación entre el Sombrerero y Alicia, y en algún momento la frase de la «muchedad» | **hay que conseguirlo** — y no se sabe de quién son las voces, ni en qué idioma, ni de dónde sale la grabación | **La única escena de la obra sin música.** El mayor sound design después del latido, y el peor material: es lo único que no se puede fabricar |
| 04 | el tramo de la escena reproducido hacia atrás con efecto de VHS, varias veces | **de la pista** — «Lo llaman vida» (P-07) invertido, y hay que elegir el tramo | ¿cuántas veces? `TODO` en la escaleta |
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
con su cue.

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

Así que **ninguno de los dos cues tiene número.** No es que sean provisionales: es que los
números no se conocen. Se asignan al pasar a `revisada`, en orden de llegada.

- **El orden es el de llegada a `revisada`, no el de la obra.** Si la 12 se revisa antes que la
  05, la 12 se lleva los cues bajos y la 05 los altos, aunque en la obra la 05 suene antes. No
  es un error: el número identifica un sonido, no su posición.
- **Un número no se reutiliza, no se renumera y no se reasigna.** Nunca.
- **Una escena que vuelve a `boceto` no mueve los cues que ya tenía.** Si el efecto cambia, el
  viejo se marca `caído`, su número queda libre para siempre, y el nuevo coge el siguiente
  número libre.
- **El `S-nn` solo vive en este fichero** (`AGENTS.md`, commit `bc74532`). En el libreto va el
  nombre del sonido tal como lo oye el público. Así el número no puede desincronizarse: está en
  un sitio.
- **`AGENTS.md` sigue usando `S-01` y `S-14` en su ejemplo del latido.** Como ejemplo está bien,
  pero **los números concretos no se pueden saber hoy**, y un número escrito en un ejemplo es un
  número que la siguiente sesión copia. `TODO(preguntar):` que el ejemplo los llame «el cue de
  la 01» y «el cue de la 11», y que diga que el 11 *podría* ser el segundo o el séptimo.

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
cue recibe su número, y ese número **no se puede reutilizar nunca**. Si el efecto después no se
puede construir —porque la grabación no llegó, porque el archivo no existe, porque era una
persona que no vino—, se marca `caído` y el número queda libre para siempre. Se ha gastado un
número en una promesa.

**Ya está pasando, y en la peor escena.** La 03 es un **audio de diálogo entero**: la
conversación entre el Sombrerero y Alicia, con la palabra «muchedad». Ahora mismo no sabemos de
quién son las dos voces, en qué idioma, ni de dónde sale la grabación. Es un material que hay
que **conseguir**, no fabricar. Si la 03 pasara a `revisada` mañana, su cue se numeraría sin
nada detrás.

**Y en el latido, que es más pequeño pero es nuestro.** La 01 está en `boceto` con la fuente
**sin decidir**: ¿el MIDI sintetizado o el bombo de la pista? Si la 01 pasara a `revisada` así,
el cue se numera con la fuente abierta, y el número se gasta en una elección que todavía no está
hecha.

**Tres salidas, y la que recomiendo es la primera:**

1. **El material tiene que existir antes de `revisada`.** La puerta pasa a ser una puerta de
   producción y no solo de escritura: `revisada` significa *el texto está y sé lo que voy a
   construir*. El coste es honesto —algunas escenas se quedan en `boceto` esperando una
   grabación— y el beneficio es que ningún número se gasta en nada.
2. **La puerta no mira el material** y se acepta que un cue numerado pueda ser inconstruible. Es
   legal según la regla, pero es un número en un sobre vacío.
3. **El número es provisional hasta que el material existe.** Rompe «la numeración es sagrada»
   desde el primer día, así que no lo recomiendo.

La (1) se consigue casi gratis: el mensaje de cuatro cosas que ya existe incluye «qué se oye»;
si además incluye **«de dónde sale el material»**, la puerta verifica sola lo que le importa.
`TODO(preguntar):` al autor y a Datos, que es `AGENTS.md` suyo.

### Los cues del disco

Son las nueve pistas con su número de pista. El orden es el de `guion/escaleta.md`, y **las nueve
quedan colocadas**.

| Cue | Escena | Pista | # | Duración |
|---|---|---|---|---|
| P-02 | 01 | «Avivas el fuego» | 02 | 6:41 |
| P-05 | 02 | «Está bien» | 05 | 3:17 |
| — | 03 | **sin disco**: audio de diálogo | — | — |
| P-07 | 04 | «Lo llaman vida» | 07 | 3:49 |
| P-03 | 05 | «On s'en fout» | 03 | 4:37 |
| P-04 | 06 | «La Reina» | 04 | 5:18 |
| P-08 | 07 | «La puerta» | 08 | 4:43 |
| P-01 | 08 | «Ser artista» | 01 | 3:58 |
| P-06 | 09 | «Vuela» | 06 | 3:33 |
| P-09 | 10 | «Seica» | 09 | 4:55 |
| P-02 | 11 | «Avivas el fuego», segunda vez | 02 | 6:41 |
| P-05 | 12 | «Está bien», segunda vez | 05 | 3:17 |

**El disco se abre y se cierra con las mismas dos canciones, en espejo**: la p. 02 abre (01) y
cierca (11); la p. 05 abre (02) y cierra (12). Es la misma forma que el espejo de las escenas
(`guion/escaleta.md`), y es lo que hace que la obra suene a disco y no a lista de reproducción.

`investigacion/referencias.md` tiene la tracklist con su fuente.

## El latido — escenas 01 y 11

El primer sound design de la obra, y el que fija el patrón de todos los demás.

### Lo que dice el libreto

Los dos libretos dicen **lo mismo, con las mismas palabras**:

> `01-el-latido.md`: `>> un latido. Muy cerca, como si fuera dentro de un cuerpo`
> `11-el-fuego.md`: `>> un latido. Muy cerca, como si fuera dentro de un cuerpo`

(En los dos ficheros había además un `>> [S-01]` y un `>> [S-14]` delante. Ya no van: el número
solo existe en `recursos/sonido.md` desde el commit `bc74532` de `AGENTS.md`. Lo que se conserva
de esos números es que **son dos cues distintos del mismo sonido**.)

Y en los dos, el latido y la música están **en el mismo sitio del texto** — el latido se anuncia,
y la pista entra justo después:

> `01`: `>> ♪ «Avivas el fuego» (p. 02)` … `**el corazón** (sigue. es el mismo latido que al final de la obra)`
> `11`: `>> ♪ «Avivas el fuego» (p. 02)` … `(el mismo latido. es el mismo corazón del principio de la obra)`

Las dos escenas tienen la misma forma: **el latido solo, un rato, y luego la música entra.** Lo
que cambia entre la 01 y la 11 no es el sonido: es todo lo que hay alrededor (el propio libreto
lo dice: «el latido no ha cambiado, el mundo sí»). Por eso el cue de la 11 es el mismo sonido con el
mismo tratamiento, y no una versión nueva.

> El «(sigue)» del 01 se leía antes como que el latido **seguía por encima de la canción**. Ya
> está resuelto: no. Ver «Lo que está decidido».

### Lo que está decidido (respuesta de Guion, 2026-09-28)

> «el latido se oye solo en el silencio de antes, y desde que entra la pista ya no hay nada que
> recortar — es la misma pista en las dos escenas. Lo que se puede cortar es cuánto dura la
> escena, no el latido.»
> — `11-el-fuego.md`, `TODO` de «¿Dónde entra la pista?»

**El latido no suena encima de la música. Suena antes, y la pista lo sustituye.** La lectura (A)
de las dos posibles, y la (B) queda fuera.

Esto tiene una consecuencia inmediata: el **«(sigue)» del libreto no quiere decir que el latido
continue sobre la canción**, sino que el latido se ha convertido en la canción. La misma
función armónica, la misma posición en el compás, el mismo sostén: ahora lo sostiene el bombo de
la pista. La frase «el latido se oye solo en el silencio de antes» es exactamente la forma
técnica de decirlo.

### Qué cambia con esto

**El latido sintetizado en MIDI pasa a ser la opción correcta.** Se descartó cuando parecía que
iba a tener que sonar seis minutos y medio por encima de «Avivas el fuego», compitiendo con
ella. No es el caso: solo tiene que soar en el negro, solo, antes de la pista. Y en esa
condición es un sonido expuesto —nada lo tapa— así que **la cola de reverberación se oye
entera**. Por eso el «cuerpo, no caverna» pasa de ser una corrección de gusto a ser
obligatorio: de 28 s a 5-7 s.

**La pista no se recorta, así que no hace falta un segundo cue de música.** `P-02` dura lo que
dura la pista, en las dos escenas, y lo que se decide es cuánto dura la escena, que es una
cosa de dramaturgia y no de sonido. Esto cierra uno de los `TODO` que tenía abiertos.

**El relevo del latido a la pista es la única parte técnica de verdad.** Un cue se para y otro
empieza, y entre los dos hay un momento. `TODO(preguntar):` cómo se hace el relevo.

**El silencio de la 11: corto, según Guion (2026-09-28).**

El texto de la 11 pone la pista en «un árbol brota», que está después de las profundidades, del
círculo que se cierra, de la *pac-man* y de las cerezas. Leído al pie, eso son minutos de latido
solo. La propuesta de Guion es que **no**, y que lo que va antes de la pista sean **dos o tres
golpes, no trece**: el negro entra igual que en la 01, y todo lo demás —el feto, el círculo, la
*pac-man*, las cerezas, la superficie, el paisaje— pasa **bajo** la pista.

Los tres argumentos que dan, y el segundo es el bueno:

1. El espejo tiene que aguantar **en el tiempo**, no solo en el contenido. Si la 01 es un
   corazón solo y enseguida la canción, y la 11 son minutos de corazón antes de la misma
   canción, las dos escenas se parecen en lo que muestran y no en lo que duran.
2. **Lo que cierra la obra es que el público reconozca la canción.** Tiene que oír «Avivas el
   fuego» y pensar *esa es la de antes*. Con minutos de latido delante no la reconoce: oye un
   latido que se le ha olvidado. **El reconocimiento es el espejo.**
3. Los 6:41 son el bloque más largo de la obra y ahí es donde tiene que caer el peso.

> **No construir el `Repitch` todavía.** Con el negro corto no hace falta, y era justo lo que
> había que prever antes de construir. `TODO(preguntar):` es propuesta de Guion, no decisión del
> autor, que está preguntado en su hilo.
>
> **Y si el autor quiere el negro largo, la 01 también tiene que alargarse.** Si no, las dos
> escenas dejan de ser el mismo espejo. Eso ya no es una decisión de la 11: es de las dos.

### Lo que abre el negro corto

**Los 6:41 de la 11 cargan con toda la escena.** Si la pista entra pronto, el feto, el círculo,
la *pac-man*, las cerezas, la superficie, el paisaje árido, el árbol que brota, los demás detrás
y la vuelta a las profundidades pasan **todo bajo la misma pista**. Es el bloque más largo de la
obra y es el pago del tercer acto, así que la imagen y la música tienen que caber una en la otra.

De ahí una pregunta que es de las dos sesiones: **¿el árbol que brota tiene que caer en un
momento concreto de «Avivas el fuego»?** Si es así, hay que saber cómo es la pista por dentro y
hay que decidir si la imagen va clavada a un compás o si se mueve libre sobre ella.
`TODO(preguntar):` a Guion.

### El punto que sigue abierto: ¿el cuerpo crece en la 11?

La pregunta es real y sigue viva. `11-el-fuego.md` la plantea bien y bien atribuida: el latido
se oye solo en el negro, y en la 11 ese mismo latido tiene delante un paisaje. ¿Basta con eso, o
el sonido **cambia** —cola larga, exterior, distancia, haciéndose paisaje?

| | El sonido no cambia | El cuerpo crece |
|---|---|---|
| Qué hace | los dos cues idénticos, byte a byte | el de la 11 es la misma fuente con la cola más larga |
| Qué dice la escena | «el latido no ha cambiado, el mundo sí» | el cuerpo se hace paisaje |
| Riesgo | el final podría sonar repetido si el público no ve el cambio | el espejo se rompe en lo que la obra dice que no se rompe |

Mi recomendación sigue siendo la primera, y ahora con un argumento más: la propia escena 11
tiene ya escrito `(el latido se ha convertido en la canción. ya no se oye aparte: es la música)`.
Si además el latido *suena* distinto en la 11, ese texto miente, porque no se ha convertido en
la canción: sigue siendo un sonido. Con el mismo sonido en las dos escenas, la frase es
exactamente cierta. `TODO(preguntar):` decide el autor.

### Propuestas (no son decisiones)

- **El fondo de sala debajo del latido** en las dos escenas, y solo en ellas: con la escena
  reducida a negro y un latido, el silencio absoluto de la sala suena a avería. En la 11 encima
  entra la pista y la sala se apaga sola. `TODO(preguntar):` el autor decidió «con algo debajo»
  antes de que la 01 se quedara en negro; hay que confirmar que sigue queriéndolo.
- **Tres golpes distintos en vez de uno en bucle**, en filas separadas. Con el negro corto ya no
  hace falta el `Repitch` para que el silencio tenga variación, pero tres golpes en vez de uno lo
  hacen mejor y de forma más barata: tres cues, tres sonidos, tres filas.

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
  un cue en nada. Ya pasa en la 03 (audio de diálogo, nadie sabe de quién son las voces) y en la
  01 (la fuente del latido está sin decidir). Recomiendo que el material exista antes de la
  puerta. Ver «El hueco de la puerta».
- **¿El cuerpo crece en la 11?** Si el latido suena distinto en la 11, es un segundo tratamiento
  y hay que construirlo. Propuesta de Ableton: que no cambie, y que crezca el mundo. Ver «El
  punto que sigue abierto».
- **¿Negro corto en las dos escenas?** Propuesta de Guion: dos o tres golpes antes de la pista,
  igual en la 01 y en la 11. **Si se quiere el negro largo, la 01 también tiene que alargarse**,
  o las dos dejan de ser el mismo espejo. De esto depende si el latido necesita `Repitch` — de
  momento **no se construye**.
- **¿El árbol brota en un momento concreto de «Avivas el fuego»?** Si la imagen va clavada a un
  compás hay que conocer la pista por dentro; si se mueve libre sobre ella, el operador lanza y
  la imagen sigue. Pregunta para Guion. Ver «Lo que abre el negro corto».
- **El relevo del latido a la pista.** El latido suena en el negro y la pista lo sustituye, así
  que hay un momento en que uno para y el otro entra. ¿Corte seco a un golpe? ¿El latido se
  ahoga justo cuando entra la pista? ¿Se solapan medio compás? Es lo único técnico que queda
  del latido.
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

- **La escena 03 es la única sin música, y es un audio de diálogo entero.** Es el segundo sound
  design de la obra por tamaño. `TODO(preguntar):` de quién son las dos voces, en qué idioma, y
  de dónde sale la grabación: es un material que hay que conseguir, no fabricar. Los derechos
  van a `Datos`.
- **La numeración S-nn.** Cambiada por la puerta de `revisada` (commit `86a26f5`): el número se
  asigna cuando la escena llega a `revisada`, en orden de llegada y no de obra, y no se
  reutiliza ni se renumera nunca. `TODO(preguntar):` la secuencia de escritura del número, que
  va de esta sesión a `sonido.md` a Guion y de ahí al libreto, y que no está en `AGENTS.md`.
- **El eco.** Si la sala tiene reverberación, ¿el disco entra por el PA directamente o pasa por
  Live? Afecta a toda la arquitectura, y en la 01 y la 11 más que en ningún otro sitio: son
  escenas con mucho silencio.
- **El Set no existe todavía.** Pistas, buses, retornos, master, key mapping: sin decidir. La
  columna «Cómo en Live» de la tabla está vacía a propósito. Falta con qué superficie de control
  se opera en escena.
- **Qué material hay grabado.** No hay inventario. ¿Qué sounds, qué field recordings, qué hay en
  el móvil de alguien?
