# FORESTGUARD

Simulador académico de prevención forestal mediante patrones fractales y distribución de sensores. Aplicación estática construida con HTML5, CSS3 y JavaScript puro.

> **Importante:** FORESTGUARD es una simulación educativa. Utiliza datos generados localmente y no detecta incendios reales ni reemplaza sistemas profesionales de monitoreo.

## Estructura

```text
FORESTGUARD/
├── index.html
├── styles.css
├── script.js
└── README.md
```

## Ejecutar localmente

1. Descarga o clona este repositorio.
2. Abre la carpeta `FORESTGUARD`.
3. Haz doble clic en `index.html` o ábrelo desde tu navegador.
4. No requiere instalación, servidor, backend ni base de datos.

Se recomienda Chrome, Edge o Firefox actualizado. La fuente web se carga desde Google Fonts; si no hay conexión, se usarán fuentes alternativas del sistema.

## Publicar gratis en GitHub Pages

1. Inicia sesión en [GitHub](https://github.com/) y crea un repositorio nuevo, por ejemplo `forestguard`.
2. Sube `index.html`, `styles.css`, `script.js` y `README.md` a la raíz del repositorio.
3. Entra a **Settings → Pages**.
4. En **Build and deployment**, selecciona **Deploy from a branch**.
5. Elige la rama `main` y la carpeta `/ (root)`. Pulsa **Save**.
6. Espera unos minutos. GitHub mostrará una dirección similar a `https://TU-USUARIO.github.io/forestguard/`.
7. Abre esa dirección para comprobar la aplicación.

Cada vez que actualices los archivos y hagas `commit`/`push`, GitHub Pages publicará los cambios automáticamente.

## Módulos

1. **Configuración del bosque:** permite definir dimensiones, sensores disponibles, presupuesto, riesgo y alcance.
2. **Simulador de fractales:** dibuja árbol binario, triángulo de Sierpinski y cuadrícula tipo Menger con profundidad ajustable.
3. **Distribución de sensores:** genera ubicaciones, conexiones por proximidad e inspección individual de nodos.
4. **Análisis de cobertura:** divide el terreno en 280 celdas, calcula cuáles están dentro del radio de al menos un sensor y clasifica el riesgo.
5. **Presupuesto y resultados:** calcula costos referenciales y compara cobertura de los tres patrones con un gráfico Canvas.

## Matemática Discreta aplicada

### 1. Recursividad
Los generadores de patrones se definen mediante funciones que se llaman a sí mismas con una profundidad menor. La condición de parada es `n <= 0`.

### 2. Recurrencias
- Árbol fractal: `T(0)=1`, `T(n)=2T(n-1)+1`.
- Sierpinski: `T(0)=1`, `T(n)=3T(n-1)+1` para el conteo de triángulos dibujados por el algoritmo.
- Cuadrícula: `T(0)=1`, `T(n)=8T(n-1)+1` para las subdivisiones conservadas.

La tabla muestra los valores generados para cada nivel. El árbol fractal binario produce `2^(n+1)-1` segmentos si se cuenta también el segmento inicial.

### 3. Árboles
El panel de llamadas presenta una representación jerárquica de las invocaciones recursivas. Cada nodo es una llamada; los nodos hoja representan el caso base. Para que la interfaz sea legible, la vista del árbol limita la expansión visual a tres niveles, aunque el fractal se calcula con la profundidad elegida.

### 4. Grafos
La red se representa como `G=(V,E)`. Cada sensor es un vértice y se crea una arista si la distancia euclidiana entre dos sensores es menor o igual a `1.8 × alcance`. Se calculan número de vértices, aristas, grado promedio y componentes conexas.

### 5. Vecino más cercano
Al hacer clic en un punto del mapa se calcula la distancia euclidiana a todos los sensores:
`d(P,S)=√((xS−xP)²+(yS−yP)²)`.
Se selecciona el sensor que minimiza esa distancia y se muestran su identificador y la distancia obtenida.

## Supuestos del modelo

- El terreno es rectangular y se expresa en unidades abstractas.
- El mapa de cobertura usa una malla de 20 × 14 = 280 sectores.
- Un sector se considera cubierto si su centro está a una distancia menor o igual al alcance de algún sensor.
- El riesgo bajo/medio/alto se asigna mediante una función determinista seudoaleatoria para que el escenario sea reproducible dentro de la sesión.
- El costo por sensor está fijado inicialmente en S/ 150 y puede cambiarse editando `COST_PER_SENSOR` en `script.js`.
- La comparación usa el mismo número de sensores, alcance y dimensiones para los tres patrones; es una estimación simplificada para fines académicos.

## Personalización

- Cambia el costo unitario en `script.js`: `const COST_PER_SENSOR = 150;`
- Ajusta el máximo de sensores o profundidad en los atributos HTML `max`.
- Cambia colores, tamaños y espaciados desde las variables CSS declaradas al inicio de `styles.css`.

## Licencia

Material de demostración académica. Puedes modificarlo y adaptarlo a tu exposición.
