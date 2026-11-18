# Contador WOD 2.2.0 — versión de producción

## Incluye

- VUELTAS: contador original 2.1 (cronómetro, estadísticas, pausa, deshacer, CSV, sonido).
- AMRAP: tiempo descendente, rondas y repeticiones extras.
- FOR TIME: cronómetro ascendente, vueltas, finalización manual y cap opcional.
- EMOM: intervalos automáticos y registro de intervalos completados.
- TABATA: alternancia programable de trabajo y descanso.
- Pantalla encendida opcional mientras el entrenamiento está en marcha (si iOS lo permite).
- Audio para eventos mientras la aplicación está activa, persistencia en `localStorage` y caché sin conexión.

## Antes de publicar

1. En el repositorio principal `contador-wod`, crear etiqueta **v2.1.0** sobre el último commit de la versión 2.1; no etiquetar todavía el código 2.2.
2. Exportar en CSV la sesión del contador 2.1 que se desee conservar. Si hay una sesión corriendo, finalizarla o pausarla antes de actualizar.
3. Mantener el repositorio `contador-wod-beta` sin cambios como referencia de pruebas.

## Publicación

1. Descomprimir el ZIP de producción.
2. Subir los **9 archivos** directamente a la raíz del repositorio principal `contador-wod`; sobrescribir los homónimos y confirmar el commit.
3. GitHub Pages debe seguir apuntando a la rama `main` y la carpeta `/(root)`.
4. Abrir con internet la aplicación instalada en el iPhone. Si todavía muestra la 2.1, cerrar/abrir con internet y comprobar si se ha activado el nuevo service worker. No borrar datos ni desinstalar la app como primera medida.
5. Repetir pruebas de humo: abrir, sesión original intacta, AMRAP, modo avión, sonido y pantalla encendida.
6. Si funciona, crear etiqueta **v2.2.0** para identificar el commit publicado.

## Persistencia y precauciones

- Clave del contador original: `contador-vueltas-v2`. **No se cambia**.
- Claves adicionales de los nuevos modos: `contador-wod-v2.2-session`, `contador-wod-v2.2-preferences`.
- La beta usaba claves separadas. Sus sesiones de prueba **no se transfieren automáticamente** a producción.
- Las sesiones se guardan solo en el navegador/dispositivo; borrar los datos del sitio o eliminar la app puede borrarlas.
- iOS puede impedir sonidos en segundo plano o denegar Screen Wake Lock.
- La actualización del service worker puede precisar volver a abrir la aplicación con conexión; no es necesario reinstalarla.
