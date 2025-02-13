# Paris transport mobility

This work is a preliminary analysis of paris mobility system through network spatial analysis. 

## Analysis Pipeline

The pipeline consists of several steps described below:

### 1. Preprocessing Paris Arrondissement Shapefiles

To ensure a more consistent analysis, we removed green spaces from the spatial file of Paris arrondissements. This provides a more accurate representation of urbanized areas and avoids distortions in distance calculations.

### 2. Generating Random Points with Poisson Disk Sampling

We distributed 100 points randomly across the Paris map using the **Poisson Disk Sampling** algorithm. This method ensures that points are evenly distributed and that the minimum distance between each point is approximately 1.1 km, preventing excessive clustering and overlaps.

### 3. Distance Calculation with Google Maps API

To obtain a realistic measure of urban connectivity, we used the **Google Maps API** to calculate travel times between all generated points. The calculations were performed using only public transport to reflect real city mobility conditions.

### 4. Creating an Interactive Map

We developed an interactive map that visualizes the connections between points based on travel times. The map allows users to explore the connections and better understand accessibility relationships between different areas of the city.

### 5. Travel Time Analysis by Arrondissement

We aggregated the data to calculate:

- The **average travel time** between points within each arrondissement.
- The **maximum travel time** for each arrondissement to identify areas with higher travel difficulty.

## Visualization

The interactive maps can be found here:
- <a href="https://savaij.github.io/map_paris/mappa_interattiva.html" target="_blank">connections map</a>
- <a href="https://public.flourish.studio/visualisation/21416572/" target="_blank">times map</a>
- <a href="https://savaij.github.io/map_paris/paris_buffers.html">buffer map</a>

The static visualizations and data can be found here:
- <a href="https://savaij.github.io/map_paris/reached_nodes.png" target="_blank">reached nodes graph</a>
- <a href="./static_maps_data/arrondissements_areas.csv" target="_blank">data</a>


This repository has the following structure:

```console
├── coordinates
│   └── coord_par_100.json
├── mappa_interattiva.html
├── matrices
│   ├── matrice_distanze_100.npy
│   └── matrice_durate_100.npy
├── notebooks
│   ├── analysis.ipynb
│   ├── coordinates.ipynb
│   ├── richieste API.ipynb
│   └── shapefiles_processing.ipynb
├── paris_buffers.html
├── readme.md
├── shapefiles
│   ├── espaces_verts.geojson
│   ├── paris_arrondissement.geojson
│   └── paris_arrondissement_no_green.geojson
├── static_maps_data
│   ├── arrondissements_areas.csv
│   ├── paris_times.geojson
│   └── reached_nodes.png
└── tex_report

```

