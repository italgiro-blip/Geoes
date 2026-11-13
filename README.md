# GeoES – Visor Interactivo de Comunidades Autónomas

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Leaflet](https://img.shields.io/badge/Leaflet-199900?style=flat&logo=leaflet&logoColor=white)
![GeoJSON](https://img.shields.io/badge/GeoJSON-4CAF50?style=flat&logo=geojson&logoColor=white)

Mapa web interactivo de España para visualizar **tasas hipotéticas** por Comunidad Autónoma. La aplicación está basada en **HTML, CSS y JavaScript**, utiliza **Leaflet** como biblioteca de mapas y carga datos geoespaciales en formato **GeoJSON**. La clasificación de los valores se realiza mediante **métodos estadísticos** (Jenks, intervalos iguales, cuartiles), que pueden cambiarse dinámicamente desde la barra lateral.

---

## 📋 Índice

- [Descripción](#-descripción)
- [Funciones](#-funciones)
- [Demo](#-demo)
- [Tecnologías](#-tecnologías)
- [Estructura del proyecto](#-estructura-del-proyecto)
- [Instalación y uso](#-instalación-y-uso)
- [Uso de la interfaz](#-uso-de-la-interfaz)
- [Clasificación estadística](#-clasificación-estadística)
- [Paletas de colores](#-paletas-de-colores)
- [Formato GeoJSON](#-formato-geojson)
- [Personalización](#-personalización)
- [Roadmap](#-roadmap)
- [Licencia](#-licencia)
- [Autor](#-autor)

---

## 📖 Descripción

**GeoESPAÑA** es un visor de mapas interactivo de las **17 Comunidades Autónomas** de España (más las ciudades autónomas de Ceuta y Melilla, si se incluyen en el GeoJSON). El mapa se renderiza con **Leaflet** y se rellena mediante un archivo GeoJSON con los límites autonómicos. Cada Comunidad Autónoma se colorea según una **tasa hipotética** (`Tax_rate`). La clasificación de los valores en clases de color se realiza mediante **métodos estadísticos** seleccionables, de modo que los mismos datos pueden mostrarse de forma distinta según el procedimiento elegido.

La aplicación sirve como material didáctico para **clasificación de datos**, **mapas de coropletas** y **visualización geoespacial**.

---

## ✨ Funciones

- 🗺️ Mapa interactivo de España con **Leaflet**.
- 🎨 Tres **métodos de clasificación estadística**: Jenks, intervalos iguales, cuartiles.
- 🌈 Cuatro **esquemas de color**: gamas de azul, rojo, lila y verde.
- 🛰️ Tres **mapas base**: Satélite (Esri), OpenStreetMap, CartoCDN Dark.
- 📥 **Importación de capas** mediante un botón (`IMPORTAR CAPA`) – recarga el archivo GeoJSON.
- 🔍 **Selección de Comunidad Autónoma** mediante un menú desplegable.
- 📊 **Cuadro informativo** con la unidad administrativa y el valor actual.
- 🖱️ **Tooltip al pasar el ratón** sobre cada Comunidad Autónoma.
- 📱 Diseño responsive con barra lateral e imágenes laterales.

---

## 🖥️ Demo

La aplicación requiere un servidor local, ya que el archivo GeoJSON se carga mediante `fetch()`.

```bash
# Opción 1: Python
python -m http.server 8000

# Opción 2: Node.js
npx serve .
```

---

## 🛠️ Tecnologías

| Tecnología | Versión | Uso |
|------------|---------|-----|
| HTML5 | — | Estructura de la interfaz |
| CSS3 | — | Estilos y diseño responsive |
| JavaScript (ES6+) | — | Lógica de la aplicación |
| [Leaflet](https://leafletjs.com/) | 1.9.x | Biblioteca de mapas interactivos |
| GeoJSON | — | Formato de datos geoespaciales |
| [simple-statistics](https://simple-statistics.github.io/) | 7.x | Cálculo de Jenks y cuantiles |

---

## 📁 Estructura del proyecto

```
geoespaña/
│
├── index.html              # Página principal
├── css/
│   └── styles.css          # Estilos de la aplicación
├── js/
│   ├── app.js              # Lógica principal (mapa, capas, eventos)
│   ├── classification.js   # Métodos de clasificación estadística
│   └── palettes.js         # Paletas de colores
├── data/
│   └── comunidades.geojson # Límites de las Comunidades Autónomas
├── img/
│   └── (imágenes laterales)
└── README.md
```

---

## ⚙️ Instalación y uso

1. **Clona el repositorio:**

   ```bash
   git clone https://github.com/tu-usuario/geoespaña.git
   cd geoespaña
   ```

2. **Inicia un servidor local** (necesario por `fetch()`):

   ```bash
   # Opción 1: Python
   python -m http.server 8000

   # Opción 2: Node.js
   npx serve .
   ```

3. **Abre el navegador** en `http://localhost:8000`.

---

## 🖱️ Uso de la interfaz

| Elemento | Acción |
|----------|--------|
| **Menú desplegable** | Selecciona una Comunidad Autónoma y centra el mapa en ella |
| **Método de clasificación** | Cambia entre Jenks, intervalos iguales y cuartiles |
| **Paleta de colores** | Cambia el esquema de color (azul, rojo, lila, verde) |
| **Mapa base** | Cambia entre satélite, OpenStreetMap y CartoCDN Dark |
| **Botón `IMPORTAR CAPA`** | Recarga el archivo GeoJSON |
| **Hover sobre el mapa** | Muestra un tooltip con el nombre y el valor |
| **Cuadro informativo** | Muestra la unidad administrativa y el valor actual |

---

## 📊 Clasificación estadística

La aplicación permite clasificar los valores de `Tax_rate` mediante tres métodos:

### 1. Jenks (Natural Breaks)
Minimiza la varianza dentro de cada clase y maximiza la varianza entre clases. Ideal para datos con distribuciones irregulares.

### 2. Intervalos iguales
Divide el rango de valores en clases de igual amplitud. Sencillo, pero sensible a valores atípicos.

### 3. Cuartiles
Divide los datos en cuatro grupos con el mismo número de observaciones. Útil para comparar posiciones relativas.

---

## 🎨 Paletas de colores

| Paleta | Colores |
|--------|---------|
| **Azul** | `#f7fbff` → `#08306b` |
| **Rojo** | `#fff5f0` → `#67000d` |
| **Lila** | `#fcfbfd` → `#3f007d` |
| **Verde** | `#f7fcf5` → `#00441b` |

Cada paleta contiene **5 clases** de color, asignadas automáticamente según el método de clasificación elegido.

---

## 🗺️ Formato GeoJSON

El archivo `data/comunidades.geojson` debe contener una `FeatureCollection` con una `Feature` por Comunidad Autónoma. Ejemplo mínimo:

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "name": "Andalucía",
        "Tax_rate": 21.5
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[...]]]
      }
    }
  ]
}
```

**Propiedades requeridas:**

| Propiedad | Tipo | Descripción |
|-----------|------|-------------|
| `name` | string | Nombre de la Comunidad Autónoma |
| `Tax_rate` | number | Valor numérico a visualizar |

---

## 🔧 Personalización

### Cambiar los valores
Edita la propiedad `Tax_rate` en `data/comunidades.geojson`.

### Añadir nuevas paletas
Edita `js/palettes.js` y añade un nuevo array de colores:

```javascript
export const palettes = {
  azul: ['#f7fbff', '#c6dbef', '#6baed6', '#2171b5', '#08306b'],
  // nueva paleta:
  naranja: ['#fff5eb', '#fdd0a2', '#fd8d3c', '#d94801', '#7f2704']
};
```

### Cambiar los mapas base
Edita el objeto de capas en `js/app.js` y añade nuevas URLs de teselas (TileLayer).

---

## 🗺️ Roadmap

- [x] Mapa interactivo con Leaflet
- [x] Clasificación estadística (Jenks, intervalos iguales, cuartiles)
- [x] Paletas de colores intercambiables
- [x] Mapas base (satélite, OSM, dark)
- [x] Tooltip y cuadro informativo
- [ ] Exportación del mapa a PNG
- [ ] Filtro por rango de valores
- [ ] Gráfico de barras con los valores por Comunidad Autónoma
- [ ] Soporte para provincias y municipios
- [ ] Modo oscuro

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia **MIT**. Consulta el archivo `LICENSE` para más información.

---

## 👤 Autor
- GitHub: https://github.com/italgiro-blip/
- Email: italgiro@gmail.com

---


