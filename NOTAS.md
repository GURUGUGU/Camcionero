# Cancionero de guitarra

App web de un solo archivo (`index.html`, antes `cancionero.html`) para usar en iPhone 16 Pro Max. Destino: `pantan.com.ar/cancionero/`.

## Qué hace hoy
- Lista de canciones, vista de canción, editor de texto, letra opcional escrita a mano.
- Acordes en Do-Re-Mi (acepta también C, Am, G7). "Mi-" = menor, "+" = aumentado.
- Diagramas de acordes como en el cuaderno de Mariano: cuerdas horizontales, 1ª arriba, trastes de izquierda a derecha.
- Posiciones propias por canción: línea `Do = x32033` (de 6ª a 1ª cuerda).
- Sugerencias de corrección en violeta: `Re{Re/Fa#}`. Al tocarlas se elige usar o dejar.
- Guardado en el teléfono (localStorage) y, con la clave puesta en Ajustes, en el servidor de Pantan: se ve igual en cualquier dispositivo y funciona sin señal (sube los cambios cuando vuelve).

## Formato de una canción
```
Título: Wish You Were Here (Pink Floyd)
Do = x32033
[Intro x2 (4/4)]
Mi- Sol Mi- Sol
```

## Decisiones
- Sin letras de canciones con derechos de autor cargadas por Claude: la letra la escribe Mariano.
- Las correcciones nunca se aplican solas: siempre como sugerencia.

## Dónde vive y cómo se publica
- La página publicada es una copia de `index.html` en el repo del sitio: `pantan-creative-lab/pantan`, en `artifacts/studio-web/public/cancionero/index.html`. Un cambio en `main` de ese repo lo publica Coolify solo, en 3 a 5 minutos.
- Las canciones se guardan en la API de Pantan (`api.pantan.com.ar/api/cancionero/canciones`), en la tabla `canciones`. Código en `artifacts/api-server/src/cancionero/rutas.ts`.
- Clave: `CLAVE_CANCIONERO` (variable de entorno de la API en Coolify, 24 caracteres o más). Claude, desde una sesión, entra con `CLAVE_ANALISTA`, así puede cargar una canción que Mariano le pasa en el chat.
- Si dos dispositivos cambian la misma canción a la vez, gana el último que guarda.

## Cargar una canción desde el chat (Claude)
`PUT https://api.pantan.com.ar/api/cancionero/canciones/<id>` con `Authorization: Bearer <clave>` y `{"texto": "Título: …\n[Intro]\nDo Sol"}`. El id: letras, números, `-` o `_`. Sin `letra` en el cuerpo, la letra que ya tenía no se toca. Antes de subir, mostrarle a Mariano cómo queda y que confirme.

## Próximos pasos (de a uno)
1. ~~Publicar en pantan.com.ar/cancionero/~~ (hecho, 03-10-2026).
2. ~~Guardar las canciones en el servidor~~ (hecho; falta cargar `CLAVE_CANCIONERO` en Coolify).
3. Modo tocar con micrófono: detectar el acorde siguiente y scrollear solo, con respaldo de avance por toque.
4. Botón para cargar canciones desde una foto del cuaderno.
