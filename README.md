# ECOFRACTAL — Laboratorio de Diseño Arquitectónico Fractal

Aplicación web estática para GitHub Pages. Permite diseñar una estructura conceptual con curva de Koch, paneles triangulares de Sierpinski y soportes ramificados, visualizarla en 3D y explorar estimaciones solares y de ventilación.

## Publicar en GitHub Pages

1. Descarga y descomprime el ZIP.
2. Sube **todo el contenido** de esta carpeta al repositorio (incluidos `styles.css` y `app.js`).
3. Los archivos `index.html`, `styles.css` y `app.js` deben quedar en la raíz del repositorio.
4. En GitHub abre **Settings → Pages**.
5. En **Build and deployment**, elige **Deploy from a branch**, rama `main`, carpeta `/ (root)` y guarda.
6. Espera a que termine la publicación.

No requiere npm, Node ni compilación. Three.js se carga desde un CDN, por lo que la visualización 3D requiere conexión a internet.

## Funciones implementadas

- Diseñador 3D con órbita, zoom, vistas superior/frontal/lateral y ajustes de dimensiones.
- Cubierta conceptual con contorno Koch recursivo.
- Paneles formados por triángulos Sierpinski separados físicamente en la geometría 3D.
- Soportes ramificados recursivos.
- Control de iteraciones y parámetros.
- Estimación solar con fecha, latitud y hora; luz direccional y sombra proyectada en la escena.
- Estimación de sombra mediante una función geométrica simplificada.
- Estimación de caudal a través de aberturas con Q = Cd·A·√(2ΔP/ρ).
- Comparador de tres alternativas.
- Explorador de alternativas con puntuación ponderada.
- Guardado local, importación/exportación JSON, CSV e informe imprimible (Guardar como PDF).
- Laboratorio matemático y visualizaciones 2D de fractales.

## Limitaciones importantes

Esta es una herramienta conceptual educativa, no un software de ingeniería:
- La cubierta Koch se genera como contorno cerrado extruido, pero no se verifica fabricación, estabilidad ni uniones.
- Los paneles Sierpinski son geometría de triángulos sólidos separados, no un análisis de resistencia de una placa real.
- Las columnas ramificadas son formas geométricas; no validan cargas ni pandeo.
- El cálculo de sombra porcentual es una estimación simplificada; la escena 3D muestra la dirección de luz y sombras, pero no realiza una integración profesional de irradiancia.
- El modelo de ventilación estima caudal por aberturas. No es CFD y no resuelve el flujo alrededor del refugio.
- No se calcula confort térmico profesional, temperatura superficial ni sensación térmica.
- Los proyectos se guardan en el almacenamiento local del navegador, no en una cuenta o servidor.
- El PDF se genera mediante la función de impresión del navegador.

## Tecnologías

HTML, CSS, JavaScript ES Modules, Three.js y OrbitControls desde CDN. Los fractales 2D se dibujan con Canvas.
