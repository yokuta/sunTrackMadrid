# ☀️ SunTrack Madrid  
SunTrack Madrid es un proyecto de análisis urbano que modela y visualiza la exposición solar de las terrazas de hostelería en Madrid mediante datos abiertos, simulización geoespacial y visualización web interactiva.
Desarrollado en el marco de la segunda convocatoria de los Premios a la Reutilización de Datos Abiertos del Ayuntamiento de Madrid, el proyecto convierte un fenómeno urbano complejo —la sombra real sobre las terrazas— en información objetiva, medible y accesible.

---

## Qué hace este proyecto
- Localiza y modela terrazas reales en la ciudad  
- Calcula su exposición solar a lo largo del día  
- Integra contexto urbano (zonas verdes, tipología de local)  
- Lo visualiza en un visor web interactivo  
Permite responder preguntas como:
- Qué terrazas tienen sol a una hora concreta  
- Dónde hay sombra en verano  
- Qué locales combinan sombra y proximidad a zonas verdes  

---

## Cómo funciona

El proyecto se estructura como un pipeline geoespacial completo:

### 1. LiDAR y modelo urbano
Se utilizan datos LiDAR del PNOA (IGN, tercera cobertura 2022–2025) para construir un Modelo Digital de Superficie (DSM) con resolución de 1 metro por píxel, que representa edificios, vegetación y entorno urbano.

### 2. Generación de terrazas
Los datos originales de terrazas son puntos administrativos, por lo que se transforman en geometrías realistas mediante:
- Proyección a fachada usando Catastro  
- Cálculo de la dirección normal  
- Extensión hacia la acera  
- Ajuste por superficie autorizada  
- Recorte con capas de aceras y viales  

### 3. Enriquecimiento de datos
Se añaden variables adicionales:
- Tipología del local (bar, restaurante, cafetería)  
- Proximidad a zonas verdes  
- Variables para filtrado en el visor  

### 4. Simulación de sombras
Se calcula la exposición solar mediante herramientas de GRASS GIS (r.sun y r.horizon):
- Un día representativo por semana  
- Intervalos horarios entre las 06:00 y las 22:00  
- Cálculo de superficie y porcentaje en sombra  

### 5. Publicación y visualización
- Almacenamiento en formato GeoParquet  
- Publicación en Cloudflare R2  
- Visualización con Leaflet y DuckDB WebAssembly  
- Despliegue mediante GitHub Pages  

---

## Tecnologías utilizadas

- Python (GeoPandas, rasterio y librerías geoespaciales)  
- GRASS GIS  
- LiDAR PNOA  
- GeoParquet  
- Cloudflare R2  
- Leaflet  
- DuckDB WebAssembly  

---

## Visor web

El resultado final es una interfaz interactiva que permite:
- Buscar terrazas  
- Filtrar por tipo de local  
- Explorar la evolución de la sombra a lo largo del día  
- Consultar métricas de forma accesible  

---

## Datos utilizados

### Base urbana
- PNOA LiDAR (IGN)  
- Catastro  
- Cartografía de aceras y viales  

### Contexto
- Terrazas del Ayuntamiento de Madrid  
- Actividades económicas  
- Zonas verdes y callejero  

---

## Objetivo

El proyecto demuestra cómo la reutilización de datos abiertos puede transformarse en una herramienta útil para comprender el espacio público urbano, apoyar la toma de decisiones y generar productos digitales replicables en otras ciudades.

---

## Vídeos

Vídeo promocional:  
https://www.youtube.com/watch?v=XdUgupjFaqo  

Ejemplo técnico:  
https://www.youtube.com/watch?v=p7rLJ-MSCoM  

---

## Estado del proyecto

Prototipo funcional con visor web en desarrollo.