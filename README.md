# FORESTGUARD — Simulador académico de vigilancia forestal

FORESTGUARD es una aplicación web estática para explorar cómo distribuir sensores ambientales en un terreno mediante patrones fractales y conceptos de Matemática Discreta.

## Cómo abrirlo

1. Descarga o clona este repositorio.
2. Abre `index.html` en un navegador moderno, o publica los archivos con GitHub Pages.
3. Para utilizar el mapa interactivo necesitas conexión a internet (usa Leaflet y OpenStreetMap).

## Módulos

- **Panel general:** indicadores y resumen de la simulación.
- **Imagen y mapa real:** carga una fotografía aérea o satelital desde tu dispositivo, marca manualmente puntos de riesgo, visualiza los sensores sobre la imagen, explora un mapa OpenStreetMap, selecciona coordenadas o solicita tu ubicación con permiso del navegador.
- **Configuración del bosque:** dimensiones, sensores disponibles, presupuesto, riesgo y alcance.
- **Simulador de fractales:** árbol fractal, triángulo de Sierpinski y cuadrícula fractal con niveles de recursividad y tablas de recurrencia.
- **Distribución de sensores:** distribución por patrón, inspección de nodos, vecino más cercano y grafo de conexiones.
- **Análisis de cobertura:** estimación de sectores cubiertos y sin cobertura.
- **Presupuesto y resultados:** costo referencial y comparación de patrones.

## Matemática Discreta

- Recursividad para generar patrones fractales.
- Recurrencias para expresar el crecimiento de los patrones.
- Árboles para representar llamadas recursivas.
- Grafos `G = (V, E)` para modelar sensores y conexiones.
- Distancia euclidiana para encontrar el sensor más cercano.

## Uso del módulo de imagen y mapa

1. En el menú, entra en **Imagen y mapa real**.
2. Pulsa **Seleccionar imagen del bosque** y elige una foto JPG, PNG o WEBP.
3. Activa **Marcar zonas de riesgo** y toca la imagen para agregar marcas rojas. Estas marcas son manuales; no hay reconocimiento automático de incendios.
4. Los puntos verdes muestran la distribución simulada de sensores. Para cambiarla, entra a **Distribución de sensores** y vuelve a distribuirlos.
5. En el mapa, haz clic para seleccionar coordenadas. El botón **Usar mi ubicación** solicita permiso de geolocalización al navegador.

## Publicar en GitHub Pages

Sube `index.html`, `styles.css`, `script.js` y `README.md` directamente a la raíz del repositorio. En **Settings → Pages**, selecciona **Deploy from a branch**, rama `main` y carpeta `/ (root)`.

## Tecnologías

HTML5, CSS3, JavaScript, SVG, Canvas, [Leaflet](https://leafletjs.com/) y [OpenStreetMap](https://www.openstreetmap.org/).

## Limitaciones importantes

- Es un simulador académico; no detecta incendios reales ni reemplaza equipos de monitoreo forestal.
- La imagen cargada no se analiza automáticamente. El usuario coloca las marcas de riesgo manualmente.
- Los sensores se dibujan como una distribución matemática sobre la imagen; no son dispositivos físicos ni ubicaciones GPS calibradas.
- El mapa muestra cartografía de OpenStreetMap, no imágenes satelitales. La geolocalización depende del permiso del navegador y normalmente requiere HTTPS (GitHub Pages lo proporciona).
- Los datos y las imágenes cargadas no se guardan en un servidor; la imagen se mantiene en memoria del navegador durante la sesión.
- Los valores de riesgo y costos son referenciales y configurables.


## Imagen incluida
La carpeta `assets/` contiene `forest-default.png`, una imagen aérea de demostración que se muestra automáticamente en el panel y en el módulo de terreno. Mantén la carpeta `assets` junto a `index.html`, `styles.css` y `script.js` al subir el proyecto a GitHub.
