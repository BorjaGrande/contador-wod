# Contador WOD 2.2.1 — integración con Generador WOD

## Incluye

- VUELTAS: contador original 2.1 (cronómetro, estadísticas, pausa, deshacer, CSV, sonido).
- AMRAP: tiempo descendente, rondas y repeticiones extras.
- FOR TIME: cronómetro ascendente, vueltas, finalización manual y cap opcional.
- EMOM: intervalos automáticos y registro de intervalos completados.
- TABATA: alternancia programable de trabajo y descanso.
- Pantalla encendida opcional mientras el entrenamiento está en marcha (si iOS lo permite).
- Audio para eventos mientras la aplicación está activa, persistencia en `localStorage` y caché sin conexión.

## Antes de publicar

1. Conservar las etiquetas anteriores; esta versión es un parche sobre la 2.2.0 estable.
2. Exportar en CSV cualquier sesión anterior que se quiera conservar; evitar actualizar mientras un cronómetro esté en marcha.
3. Mantener el repositorio `contador-wod-beta` sin cambios como referencia de pruebas.

## Publicación

1. Descomprimir el ZIP de producción.
2. Subir los **9 archivos** directamente a la raíz del repositorio principal `contador-wod`; sobrescribir los homónimos y confirmar el commit.
3. GitHub Pages debe seguir apuntando a la rama `main` y la carpeta `/(root)`.
4. Abrir con internet la aplicación instalada en el iPhone. Si todavía muestra la 2.1, cerrar/abrir con internet y comprobar si se ha activado el nuevo service worker. No borrar datos ni desinstalar la app como primera medida.
5. Repetir pruebas de humo: abrir, sesión original intacta, AMRAP, modo avión, sonido y pantalla encendida.
6. Si funciona, crear etiqueta **v2.2.1** para identificar el commit publicado.

## Persistencia y precauciones

- Clave del contador original: `contador-vueltas-v2`. **No se cambia**.
- Claves adicionales de los nuevos modos: `contador-wod-v2.2-session`, `contador-wod-v2.2-preferences`.
- La beta usaba claves separadas. Sus sesiones de prueba **no se transfieren automáticamente** a producción.
- Las sesiones se guardan solo en el navegador/dispositivo; borrar los datos del sitio o eliminar la app puede borrarlas.
- iOS puede impedir sonidos en segundo plano o denegar Screen Wake Lock.
- La actualización del service worker puede precisar volver a abrir la aplicación con conexión; no es necesario reinstalarla.


## Integración v2.2.1
- Acepta URL `?from=generador-wod&v=1&mode=fortime&cap=15` y variantes AMRAP, EMOM y TABATA.
- Verifica rangos y crea sesión pausada/lista, sin iniciarla automáticamente.
- Soporta TABATA con descansos entre bloques enviados desde el Generador.
- Pregunta antes de reemplazar sesiones activas o terminadas. No toca datos del contador original 2.1.
- Mantiene las mismas claves de almacenamiento. Actualizar **antes** que Generador WOD v1.0.13.
