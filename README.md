# Tráiler Imperial

Convierte tu logro en una orden de rodaje para **MiniMax H3**: plano, lente, movimiento de cámara y luz ya decididos, y el prompt listo para copiar.

Hecho para los Juegos Imperiales V3 de [Imperio Agéntico](https://www.skool.com/imperio). Abierto a las tres casas.

---

## Por qué existe

H3 genera un clip de cinco segundos en menos de tres. Eso dejó de ser el cuello de botella.

El cuello es el otro: un prompt de tres líneas devuelve un video que podría ser de cualquiera. Cabe un solo movimiento de cámara en cinco segundos, y si no dices de dónde viene la luz el modelo pone la suya, que es plana y de escaparate.

La página no genera el video. Escribe la orden con la que se lo vas a pedir a H3.

## Cómo funciona

1. Eliges tu casa. Si no sabes cuál es, escribes tu apellido y te lo dice.
2. Eliges qué tipo de logro fue. Cada tipo trae su gramática de dirección.
3. Añades los planos que quieras y les pones sujeto, escala y segundos.
4. Eliges el sonido, y el diálogo si lo hay.
5. Copias el prompt y lo pegas en [fal.ai](https://fal.ai/tools/minimax-h3-max).
6. Si quieres, descargas la ficha de dirección como imagen y la adjuntas a tu logro.

### Los planos son casillas

Añades una casilla por plano. Cada una lleva qué se ve, qué tan cerca está la cámara y cuánto dura. La suma es la duración del clip, y la herramienta escribe los bloques con sus cortes.

Hay **nueve escalas** en el desplegable, de detalle a gran general, cada una con su lente y su movimiento. Ninguna casilla trae nada escrito: el desplegable rellena si lo pides, y hay un aspa para volver a dejarla vacía.

Cinco secuencias reparten planos y tiempos de golpe —el golpe (2 planos), revelar, situar y entrar, ir y volver (3 cada una), y a mi manera, que no toca nada—. Después mueves lo que quieras.

**Que H3 obedece los cortes está probado**, no supuesto: se le pidieron dos planos en cinco segundos, cerrado de manos de 0 a 2 s y general de perfil a oscuras de 2 a 5 s, y el corte cayó en el segundo 2. Lo que hace que obedezca es anunciar cuántos planos hay antes de describirlos, numerarlos con su franja de segundos, escribir `HARD CUT` en su propio renglón y dar a cada plano su propio lente. La herramienta lo escribe así.

No hay límite de segundos en la barra. H3 genera **15 segundos como máximo por vez**, así que al pasarte el prompt sale partido en generaciones de 15 s o menos, listas para pegar por separado y montar después.

### Dos costumbres que suelen ayudar

Van dentro de la herramienta como aviso, no como bloqueo. Se pueden ignorar.

- **Saltar dos escalas o más entre un plano y el siguiente.** Dos planos parecidos seguidos se leen como un brinco de cámara antes que como un corte.
- **Dar más segundos a los planos abiertos.** Un general se recorre con la mirada y eso lleva tiempo; un detalle se lee en uno. Repartir al revés suele dejar el clip lento al principio y atropellado al final.

Y el orden es la narración: de general a cerrado sitúas y entras, de cerrado a general revelas el tamaño, y empezar y terminar en el mismo plano cierra el círculo.

### Por qué listas y no un campo de texto

H3 obedece mejor en inglés, y pedirle a la gente que escriba en inglés es una barrera. Lo medimos: mismo prompt en los dos idiomas, con la misma imagen de partida. En español el movimiento de cámara y la composición salen igual de bien, pero el modelo va menos al objeto exacto —se pidió «la tecla enter» y devolvió un teclado genérico— y sigue con menos precisión las indicaciones de luz.

Con listas nadie traduce nada: eliges en español y sale inglés escrito por alguien que sabe qué pedirle a una cámara. Hay campo libre en cada plano y en la luz para quien quiera precisar.

## Las seis gramáticas

Cada tipo de logro trae decidido el plano, el lente, el movimiento y la luz:

| Logro | Plano | Movimiento | Por qué |
|---|---|---|---|
| Una herramienta | Detalle que se abre a general, 35 mm | Retroceso lento | Alejarse revela el tamaño de lo que hiciste |
| Una venta | Plano medio de manos, 50 mm | Acercamiento lento | La venta se cuenta en las manos y en la pantalla, nunca en una cara sonriendo |
| Un error que resolví | Fijo, dos tiempos en el mismo encuadre, 40 mm | Cámara quieta | Lo que cambia es la luz, de fría a cálida, y con eso se lee el antes y el después |
| Una automatización | Cenital sobre una superficie, 28 mm | Lateral constante | Un mecanismo se mira desde arriba y de corrido |
| Un hito personal | Contrapicado a contraluz, 24 mm | Tilt hacia arriba | Subir la cámara es la gramática del logro; a contraluz porque importa la silueta |
| Algo para los míos | Cerrado, 85 mm | Casi quieto | Mover la cámara aquí convierte el afecto en publicidad |

## Seis cosas que conviene saber de un plano

1. **En un plano cabe un gesto de cámara.** Si pides tres, el modelo elige uno y descarta los otros dos sin avisar.
2. **Un sujeto por plano.** Dos personas en un plano corto son dos personas mal miradas.
3. **La luz se pide o se inventa.** Nombra la fuente y la dirección.
4. **Parte el tiempo en dos.** «0–2s… 2–5s…» es lo que convierte un plano fijo en una toma con dirección.
5. **Pide lo que se ve.** La cámara no filma conceptos. «Crecimiento» no existe; una línea que sube en una pantalla, sí.
6. **El movimiento es la emoción.** Acercarse es descubrir. Alejarse es revelar el tamaño. Subir es logro. Quieto es respeto.

## El sonido

H3 genera el audio en la misma pasada que la imagen, con sincronía de labios si hay diálogo. No hay que montar nada aparte.

Vale la pena pedirlo aunque no lo parezca. Un clip generado con la línea de sonido escrita salió a **−23,4 dB**; el mismo prompt sin ella, a **−48,1 dB**, que es prácticamente mudo. Hay siete opciones de ambiente, una casilla libre para describir el tuyo, y un campo de diálogo que solo aparece en la ficha y no entra en el prompt.

Para el diálogo, en cinco segundos caben doce o trece palabras. Si escribes más, el modelo acelera o corta.

## Detalles técnicos

Un archivo. Sin dependencias, sin build, sin backend, sin llamadas a ninguna API. Reglas deterministas en JavaScript plano: el criterio de dirección está escrito en el código, no lo decide un modelo.

Pesa 136 KB, casi todo son los escudos de las tres casas en base64. Funciona en claro y en oscuro. Recuerda tu casa en `localStorage`.

Para correrlo en local:

```bash
python3 -m http.server 8080
```

## Precio de H3, para que nadie se lleve sorpresas

En `fal.ai/tools/minimax-h3-max` se prueba sin registro, con 5 segundos y 480p fijos. Con cuenta son 5 videos gratis al día.

Por la página del modelo se paga por segundo. Tarifa vigente al 1 de septiembre de 2026, leída en la propia página:

| | 480p | 768p |
|---|---|---|
| Ahora, con descuento de lanzamiento | $0,0125 / s | $0,02 / s |
| Desde el 7 de septiembre de 2026 | $0,05 / s | $0,08 / s |

Con la tarifa de ahora, diez segundos a 768p salen por veinte céntimos. Verifica el precio vigente en fal antes de montar nada encima.

## Cómo se hizo el teaser

El teaser que acompaña a esta herramienta no salió de un solo prompt, y contarlo a medias sería raro en una página que va justamente de pedirle bien las cosas a un modelo.

**Lo que hizo H3** es un clip de cinco segundos, imagen a vídeo, a 768p. Costó $0,10. La imagen de entrada fue una captura de esta misma página, y el prompt fue este, sin recortar:

```
Two hands rest on a laptop keyboard in a dark room at night. 0-2s: one finger
presses the enter key, then both hands withdraw and lower completely out of the
bottom of the frame. 2-5s: the hands are gone, the camera pulls back slowly, and
the entire laptop screen stays fully visible, unobstructed and centred, with the
dark desk and the room around it. Wide shot, 35mm lens, single continuous move.
Hard side light from one source, deep shadows. Deep cobalt blue tones from the
screen. Documentary realism, restrained, no stylization. A low sustained hum and
one soft key click.
```

Dos detalles de ese prompt salieron de equivocarse antes. El primero, pedir que las manos **se retiren por abajo del cuadro**: sin esa frase se quedan tapando la pantalla los cinco segundos. El segundo, decir que la pantalla queda **entera, sin obstrucción y centrada**: si solo se pide que la cámara retroceda, el modelo encuadra donde le parece.

**Lo que no hizo H3** es todo lo demás, y es la mayor parte:

- El texto de la pantalla en el tramo del retroceso. H3 reconstruye la interfaz de memoria y se le deshace al alejarse la cámara, así que la página real se compone encima. Se hace en 4K sobre un solo fotograma, y el movimiento se genera después sobre esa imagen: pantalla y contenido son la misma imagen, así que no pueden despegarse.
- Los seis logros de la comunidad que aparecen dentro de la pantalla. Son capturas reales, encajadas en perspectiva y con la iluminación del plano heredada por baja frecuencia, para que no se lean como una calcomanía pegada encima.
- El diseño de sonido y el montaje.

Se intentó primero seguir la pantalla fotograma a fotograma y pegar ahí la interfaz. No funciona, y la razón es interesante: esta página tiene filas repetidas —botones sobre botones, líneas de texto sobre líneas—, así que el emparejamiento encuentra soluciones desplazadas una fila con la misma puntuación, y hasta llega a confundir las filas de botones con las filas de teclas del teclado. Dibujar el resultado encima del fotograma no delata el fallo; medir la correlación entre la pantalla real y la interfaz proyectada, sí.

## Licencia

MIT. Úsalo, cámbialo, pásalo.

---

Alexander Sánchez · Casa Pegaso 🔵

[github.com/alexsanchezkb/trailer-imperial](https://github.com/alexsanchezkb/trailer-imperial) · [trailer-imperial.vercel.app](https://trailer-imperial.vercel.app)

Los escudos de las tres casas son material oficial de los Juegos Imperiales V3 de [Imperio Agéntico](https://www.skool.com/imperio). Aquí se usan tal cual, sin modificar.
