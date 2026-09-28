# Diagnóstico de Contaminación Atmosférica en Mérida, Yucatán

Visor web interactivo y adaptativo (*Responsive*) desarrollado con **Leaflet.js** para el monitoreo ambiental y ordenamiento territorial del municipio de Mérida. El proyecto espacializa la presión sobre la calidad del aire mediante un indicador que correlaciona datos satelitales con censos económicos locales a nivel de **AGEB urbana**.

## 📊 Metodología e Indicadores

1. **Procesamiento Atmosférico (GEE):** Extracción del promedio anual (2025) de densidad de columna troposférica de **Dióxido de Nitrógeno (NO₂)** usando imágenes *Level 3 OFFL* del sensor **Sentinel-5P (TROPOMI)** en Google Earth Engine, exportado como Teselas XYZ para alto rendimiento web.
2. **Densidad Económica (QGIS):** Conteo espacializado de los puntos del **DENUE** y cálculo de la densidad absoluta (establecimientos/km²) por polígono de AGEB, tras depurar la base mediante funciones SQL anidadas en UTF-8.
3. **Índice Final de Presión Atmosférica (IFPA):** Construcción de un índice compuesto normalizado (escala 0-100) que promedia la fuerza de emisión económica con el gradiente continuo del raster satelital (0.000053 a 0.000065 mol/m²).
4. **Estado del Indicador:** Clasificación cualitativa del índice numérico en 4 niveles de condición ambiental (**BAJO, MODERADO, ALTO y CRÍTICO**) mediante lógicas condicionales `CASE WHEN`.

## 🗃️ Fuentes de Información

* **Límites y AGEBs:** INEGI (2020). *Marco Geoestadístico Urbano del Municipio de Mérida*.
* **Actividades Económicas:** INEGI (2026). *Directorio Estadístico Nacional de Unidades Económicas (DENUE)*.
* **Datos Atmosféricos:** Agencia Espacial Europea (ESA) / Copernicus (2025). *Sentinel-5 Precursor*.

## 📚 Sustento de Filtrado (DENUE)

La selección exclusiva de los giros económicos con impacto directo en la atmósfera se fundamentó bajo criterios científicos internacionales:
* **Combustión y Procesos Térmicos:** Panaderías, tortillerías, plantas de concreto y energía justificadas por el *Inventario Nacional de Emisiones (SEMARNAT/INECC)* y el compendio *AP-42* de la **U.S. EPA** como precursores de \(NO_x\) y CO.
* **Compuestos Orgánicos Volátiles (COV):** Talleres de hojalatería y pintura, carpinterías y gasolineras seleccionados según las directrices de la **OMS** y la *NOM-172-SEMARNAT* por emisiones fugitivas de solventes precursores de ozono.
* **Transporte Pesado Diésel:** Centrales y encierros logísticos incluidos con base en los lineamientos de la **OCDE** por inyección concentrada de nitrógenos vehiculares.

Link del visor web: https://cesdiaz616.github.io/Contaminacion_atmosferica_Merida/. 
