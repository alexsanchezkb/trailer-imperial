# Tráiler Imperial

Convierte tu logro en una orden de rodaje para **MiniMax H3**: plano, lente, movimiento de cámara y luz ya decididos, y el prompt listo para copiar.

Hecho para los Juegos Imperiales V3 de [Imperio Agéntico](https://www.skool.com/imperio). Abierto a las tres casas.

---

## Por qué existe

H3 genera un clip de cinco segundos en menos de tres. Eso dejó de ser el cuello de botella.

El cuello es el otro: un prompt de tres líneas devuelve un video que podría ser de cualquiera. La mayoría no sabe que en cinco segundos cabe un solo movimiento de cámara, o que si no dices de dónde viene la luz el modelo pone la suya, que es plana y de escaparate.

Esta página no genera el video. **Decide cómo pedirlo.**

## Cómo funciona

1. Eliges tu casa. Si no sabes cuál es, escribes tu apellido y te lo dice.
2. Eliges qué tipo de logro fue. Cada tipo trae su gramática de dirección.
3. Eliges el sujeto y el momento de una lista. No hay que escribir en inglés: cada opción ya lo lleva dentro.
4. Copias el prompt y lo pegas en [fal.ai](https://fal.ai/tools/minimax-h3-max).
5. Si quieres, descargas la ficha de dirección como imagen y la adjuntas a tu logro.

### Por qué listas y no un campo de texto

H3 obedece mejor en inglés, y pedirle a la gente que escriba en inglés es una barrera. Lo medimos: generamos el mismo prompt en los dos idiomas, con la misma imagen de partida. En español el movimiento de cámara y la composición salen igual de bien, pero el modelo va menos al objeto exacto — pedimos «la tecla enter» y devolvió un teclado genérico — y respeta peor la luz.

Con listas nadie traduce nada: eliges en español y sale inglés escrito por alguien que sabe qué pedirle a una cámara. El campo libre sigue ahí para quien quiera precisar.

## Las seis gramáticas

Cada tipo de logro trae decidido el plano, el lente, el movimiento y la luz. No son ajustes al azar:

| Logro | Plano | Movimiento | Por qué |
|---|---|---|---|
| Una herramienta | Detalle que abre a general, 35 mm | Retroceso lento | Alejarse revela el tamaño de lo que hiciste |
| Una venta | Plano medio de manos, 50 mm | Acercamiento lento | La venta se cuenta en las manos, nunca en una cara sonriendo |
| Un error resuelto | Fijo, dos tiempos, 40 mm | Cámara quieta | Lo que cambia es la luz, de fría a cálida. Con eso basta |
| Una automatización | Cenital, 28 mm | Lateral constante | Un mecanismo se mira desde arriba y de corrido |
| Un hito personal | Contrapicado, 24 mm | Tilt hacia arriba | Subir la cámara es la gramática del logro |
| Algo para los míos | Cerrado, 85 mm | Casi quieto | Mover la cámara aquí convierte el afecto en publicidad |

## Las seis reglas de los cinco segundos

1. **Un solo movimiento.** Si pides tres, el modelo elige uno y descarta los otros dos sin avisar.
2. **Un solo sujeto.** Dos personas en cinco segundos son dos personas mal miradas.
3. **La luz se pide o se inventa.** Nombra la fuente y la dirección.
4. **Parte el tiempo en dos.** «0–2s… 2–5s…» convierte un plano fijo en una toma con dirección.
5. **Pide lo que se ve.** La cámara no filma conceptos. «Crecimiento» no existe; una línea que sube en una pantalla, sí.
6. **El movimiento es la emoción.** Acercarse es descubrir. Alejarse es revelar el tamaño. Subir es logro. Quieto es respeto.

## Detalles técnicos

Un archivo. Sin dependencias, sin build, sin backend, sin llamadas a ninguna API. Reglas deterministas en JavaScript plano: el criterio de dirección está escrito en el código, no lo decide un modelo.

Pesa 28 KB. Funciona en claro y en oscuro. Recuerda tu casa en `localStorage`.

Para correrlo en local:

```bash
python3 -m http.server 8080
```

## Precio de H3, para que nadie se lleve sorpresas

En `fal.ai/tools/minimax-h3-max` se prueba sin registro. Con cuenta son 5 videos gratis al día.

Por API, al momento de escribir esto: $0,025 por segundo a 480p y $0,04 a 768p, en tarifa promocional de lanzamiento. Verifica el precio vigente en fal antes de montar nada encima.

## Licencia

MIT. Úsalo, cámbialo, pásalo.

---

Alexander Sánchez · Casa Pegaso 🔵
