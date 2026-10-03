# Cancionero de guitarra

App web de un solo archivo (`index.html`, antes `cancionero.html`) para usar en iPhone 16 Pro Max. Destino: `pantan.com.ar/cancionero/`.

## Qué hace hoy
- Lista de canciones, vista de canción, editor de texto, letra opcional escrita a mano.
- Acordes en Do-Re-Mi (acepta también C, Am, G7). "Mi-" = menor, "+" = aumentado.
- Diagramas de acordes como en el cuaderno de Mariano: cuerdas horizontales, 1ª arriba, trastes de izquierda a derecha.
- Posiciones propias por canción: línea `Do = x32033` (de 6ª a 1ª cuerda).
- Sugerencias de corrección en violeta: `Re{Re/Fa#}`. Al tocarlas se elige usar o dejar.
- Guardado en localStorage (prototipo).

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

## Próximos pasos (de a uno)
1. Publicar en pantan.com.ar/cancionero/ desde GitHub (definir si el hosting tiene SSH o solo FTP).
2. Guardar las canciones en el servidor en lugar de localStorage.
3. Modo tocar con micrófono: detectar el acorde siguiente y scrollear solo, con respaldo de avance por toque.
4. Botón para cargar canciones desde una foto del cuaderno.
