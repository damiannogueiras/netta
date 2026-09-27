# Referencias

> Datos verificados sobre la banda y el disco, **siempre con su fuente**. Aquí no se inventa
> nada: lo que no esté en este fichero con fuente se marca `TODO(preguntar):` en el fichero que
> lo necesite.
> Los guiones llevan la obra, no los datos. Si un dato está aquí, los guiones lo pueden dar por
> cierto.

## El disco

**Estado: tracklist verificada. Metadatos del disco sin confirmar.**

| # | Título | Duración |
|---|---|---|
| 01 | Ser artista | 3:58 |
| 02 | Avivas el fuego | 6:41 |
| 03 | On s'en fout | 4:37 |
| 04 | La Reina | 5:18 |
| 05 | Está bien | 3:17 |
| 06 | Vuela | 3:33 |
| 07 | Lo llaman vida | 3:49 |
| 08 | La puerta | 4:43 |
| 09 | Seica | 4:55 |

- **9 pistas. Duración total: 40:51.**
- **Fuente:** tracklist facilitada por el autor del proyecto (captura de pantalla del reproductor),
  2026-09-27. Transcripción por OCR, contrastada con `guion/sinopsis.md`: los nueve títulos
  coinciden uno a uno con las nueve canciones que la sinopsis sitúa en la obra, lo que confirma
  la lectura de las pistas 01 y 04 («Ser artista» y «La Reina»), que en la captura no se leían
  con nitidez.

### Verificado a partir de la tracklist

- **El disco tiene 9 canciones y la obra las usa las 9.** No hay pistas de sobra ni canciones
  que se queden fuera. Esto cierra la pregunta que quedó abierta en `guion/escaleta.md`.
- **El orden de la obra no es el orden del disco.** En escena, las canciones suenan así:

  | Escena | Pista del disco | # del disco |
  |---|---|---|
  | 01 | Lo llaman vida | 07 |
  | 02 | *sin música propia* | — |
  | 03 | Avivas el fuego | 02 |
  | 04 | On s'en fout | 03 |
  | 05 | La Reina | 04 |
  | 06 | Ser artista | 01 |
  | 07 | La puerta | 08 |
  | 08 | Seica | 09 |
  | 09 | Vuela | 06 |
  | 10 | Está bien | 05 |

  Coincide en bloques: 02–05 y 07–08 mantienen el orden del disco, pero 01 (07), 06 (01) y
  09–10 (06, 05) lo invierten. **Esto es una decisión del autor, no un descuido** — pero
  todavía no está razonada en ningún sitio, y es el tipo de cosa que conviene tener escrita en
  `recursos/sonido.md` porque explica por qué el disco se oye «desordenado» en la obra.

  > **Aviso: esta tabla está desfasada.** Es de un orden anterior de la obra. El orden que
  > manda ahora está en `guion/escaleta.md` (01 «Avivas el fuego», 02 «Está bien», 07 «La
  > puerta», 08 «Ser artista», 09 «Vuela», 10 «Seica», 11 «Avivas el fuego» → «Está bien»,
  > 04 «Lo llaman vida») y su tabla de cues está en `recursos/sonido.md`. Lo verificado aquí
  > sigue en pie: la tracklist, las duraciones y los idiomas.
- **«Seica» está en gallego** (9 de 9 es la única del disco en otro idioma). «On s'en fout» está
  en francés. El resto, en español.
- **«Avivas el fuego» es la pista más larga del disco** (6:41) y ocupa la escena 03 entera,
  que es una sola imagen. Es el mayor bloque de tiempo musical de la obra: condiciona el
  ritmo y la duración total.

## Sin verificar

Nada de lo siguiente está confirmado. Procede de la sinopsis del autor y se usa en el guion,
pero necesita fuente antes de que sea un dato firme:

- `TODO(preguntar):` **Nombre del disco** y **fecha de edición**.
- `TODO(preguntar):` **Editor discográfico** (sello).
- `TODO(preguntar):` **Integrantes** de Netta Rufina y su función. La sinopsis menciona a
  «Alex, del cantante del grupo», y al final aparecen fotos de «los integrantes» siendo niños:
  el reparto de la obra depende de cuántos son.
- `TODO(preguntar):` **Autoría de las letras.** El autor del proyecto es miembro de la banda con
  derechos de autor sobre las canciones (`AGENTS.md`), pero falta saber quién firma cada una y
  si hay coautoría externa. Hace falta para `recursos/produccion.md`.
- `TODO(preguntar):` **«The Mirror».** En la escena 06 la sinopsis habla de «el disco anterior
  de algunos integrantes». ¿Es un disco de Netta Rufina, de otro conjunto, o una referencia
  a algo que ocurre en la escena? Si es un disco real, su tracklist importa (se ven imágenes
  suyas en escena).
- `TODO(preguntar):` **Autenticidad de la voz en off** de la escena 05. Si la voz es de Alex,
  ¿es una grabación existente o se graba para la obra?
- `TODO(preguntar):` **«Alicia» de Tim Burton.** La escena 02 usa un fragmento de la película.
  ¿Con qué material concreto (fragmento, póster, fotograma)? Afecta a derechos de imagen, no
  solo de música.

## Despersonalizar

**La obra ya no se personaliza en Netta Rufina.** La banda pone la música —las nueve pistas
son suyas— pero la historia que se representa no es la suya: los protagonistas no son unos
músicos concretos. Este inventario recoge lo que hay que quitar o cambiar. La decisión es del
autor (2026-09-27); la lista es consecuencia de ella.

| Escena | Qué ponía antes | Qué hay que decidir |
|---|---|---|
| 02 y 11 | Fotos de los integrantes de Netta Rufina de niños y adolescentes | Fotos de niños de alguien que no sea la banda: ¿archivo, stock, o se filma? Y si son los mismos niños en las dos escenas (la obra se cierra sobre ellos). |
| 05 | «los patos son cambiados por las caras de agobio de los integrantes de la banda» | **Resuelto:** ya no hay caras de nadie. Las dianas son **formas de discurso vacío** (queja, crítica, juicio) que no representan a nadie concreto, disparadas por el aviador. `TODO(preguntar):` qué son físicamente esas formas. |
| 06 | Voz en off del cantante (Alex) modificada tras la máscara de gas | **Resuelto:** la voz es la del **aviador**, que ya es un títere de la obra. Deja de ser la banda. Queda decidir quién la pone (casting) y si la Reina es un títere o un estado. |
| 08 | «los hombres y la mujer voladora del disco anterior de algunos integrantes (*The Mirror*)» | De quién es ese disco, o qué se pone en su lugar. Depende de qué sea *The Mirror* (ver abajo). |
| 09 | «una grabación de un concierto de Netta Rufina de cuando todavía no habían sacado el disco» | ¿Un concierto de la banda sigue valiendo, o el videoclip tiene que ser de otro grupo / de archivo? |

Lo que **no** cambia: las nueve pistas del disco, y que la banda toque y cante en escena.

## Material de imagen citado en las escenas

Estas escenas parecen construirse sobre material existente. No hay fuente para ninguna, y todas
son un problema de derechos por separado del de la música:

- Escena 02 — fragmento de *Alicia* de Tim Burton.
- Escena 03 — vídeo de «Avivas el fuego» (imagen del feto rojo, capas, *pac-man*).
- Escena 05 — imágenes de Gaza destruida y de personas desplazadas. **Cuidado con el
  tratamiento**: hay que decidir qué se muestra exactamente y con qué criterio. Ver
  `recursos/produccion.md` y el `TODO(preguntar)` de la escena.
- Escena 06 — la luna y el ojo de la película muda de Méliès.
- Escena 08 — el jabalí, la lechuza y las lobas del bosque gallego.
- Escena 09 — **el nido real de pájaros que anidó en casa** y el **vídeoclip de «Vuela»**, un
  concierto de Netta Rufina de antes del disco.
- Escena 10 — **las fotos de los integrantes de Netta Rufina de niños y adolescentes.** Material
  propio, que probablemente no dé ningún problema.

`TODO(preguntar):` ¿qué parte de este material existe ya, en qué formato, y quién lo tiene?
Sin eso no se puede escribir `recursos/escena.md`.
