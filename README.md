# Vector Geospatial Foundations for Earth Observation
This repository develops a practical foundation for working with the vector data that gives satellite imagery meaning: administrative boundaries, settlements, camps, cities, and geographic features that help turn pixels into evidence.
The accompanying notebook, [`lab02.ipynb`](lab02.ipynb), explores the territories of **Gaza, Palestine** and **Algeria** through real geographic datasets. It demonstrates how remote-sensing teams prepare, analyze, combine, and preserve spatial information before using it with satellite observations.
> The mission is not merely to draw maps. It is to build the spatial reasoning and geospatial data infrastructure needed for Earth-observation workflows.
## Research Goal
Satellite missions generate vast volumes of image data, but pixels become useful when they can be connected to the places and populations they represent. This work establishes that connection.
The notebook builds a reproducible geospatial workflow for:
- Structuring administrative boundaries as analysis-ready vector data
- Measuring geographic area and understanding territorial scale
- Calculating meaningful locations with centroids
- Mapping human settlements and populations
- Comparing spatial observations across different regions
- Preserving vector information in interoperable formats
- Preparing boundaries for future overlays with raster and satellite data
The resulting pipeline represents a small but essential part of a larger remote-sensing system: **geographic reference layers → satellite analysis → spatial evidence → decision support**.
## Regional Study Areas
### Gaza Strip
Gaza provides a compact, high-priority study area for humanitarian and urban observation. The notebook isolates five governorates, calculates their projected areas and centroids, and creates a point layer for major refugee camps.
This foundation supports future research on:
- Population exposure and displacement
- Built-up-area change
- Infrastructure damage assessment
- Access to essential services
- Humanitarian site monitoring
- Change detection between satellite acquisitions
### Algeria
Algeria provides a contrasting national-scale study area. The notebook examines wilayas, area distributions, major cities, spatial extent, and compactness.
This foundation supports future research on:
- Desert and vegetation change
- Urban growth and regional development
- Water-resource and land-use monitoring
- Large-area environmental mapping
- Climate and agricultural impact assessment
## What the Notebook Builds
The workflow in [`lab02.ipynb`](lab02.ipynb) covers five connected capabilities.
### 1. Load and Filter Earth-Observation Reference Data
- Downloads GADM administrative boundaries
- Reads GeoJSON into GeoDataFrames
- Filters and verifies Palestine's Gaza governorates
- Explores country and regional geometry
### 2. Reproject and Measure
- Converts geographic coordinates from EPSG:4326 to projected coordinate systems
- Uses UTM Zone 36N for Gaza and UTM Zone 31N for Algeria
- Calculates polygon area in square kilometres
- Computes and compares centroids
Projected coordinates are essential: latitude and longitude are stored in degrees and cannot be used directly for accurate area or distance measurements.
### 3. Construct and Overlay Point Features
- Creates point geometries from longitude and latitude
- Builds refugee-camp and major-city GeoDataFrames
- Adds population attributes
- Overlays points on administrative boundaries
These point layers can later become ground-truth locations, sample points, monitoring stations, or centers for extracting satellite observations.
### 4. Export for Interoperable Earth-Observation Workflows
The notebook produces reusable spatial products in multiple formats:
| Format | Research role |
|---|---|
| GeoJSON | Portable web mapping and lightweight exchange |
| Shapefile | Compatibility with established GIS platforms |
| GeoPackage | Modern, portable storage for boundaries and points in one container |
Generated products are written to `output/`, including Gaza governorates and camps, Algeria wilayas and cities, and a zipped download package when running in Colab.
### 5. Test Spatial Relationships
- Dissolves regional boundaries into a single territorial shape
- Builds convex hulls
- Measures compactness and geometric extent
- Identifies the northernmost and southernmost wilayas
- Verifies geometry and CRS consistency after format conversion
These operations establish the spatial relationships that later allow rasters, polygons, points, and temporal observations to be queried together.
## Future Doors
This notebook is a foundation for several research paths:
- **Satellite image alignment:** Clip Sentinel-2, Landsat, MODIS, or commercial imagery to the generated boundaries and compare conditions across regions.
- **Built-up-area change detection:** Combine national and governorate polygons with time-series imagery to quantify urban expansion or infrastructure loss.
- **Humanitarian impact monitoring:** Place refugee camps and population centers within damage or displacement observations.
- **Disaster and conflict assessment:** Detect change in settlements and infrastructure while preserving geographic and temporal context.
- **Agricultural monitoring:** Link administrative units to NDVI, crop classifications, and seasonal observations.
- **Environmental analysis:** Overlay terrain, water, land cover, fire, and climate rasters with vector boundaries.
- **Automated geospatial pipelines:** Scale the notebook into cloud processing workflows using GeoPackage, GeoParquet, STAC, Earth Engine, or cloud-native raster formats.
- **Data-quality research:** Test projection choices, boundary uncertainty, CRS transformations, and format preservation across larger datasets.
Each extension depends on the core skills demonstrated here: geodataframe construction, CRS management, spatial measurement, overlay, geometry analysis, and interoperable export.
## Repository Contents
```text
.
├── lab02.ipynb   # Reproducible vector geospatial workflow
├── README.md     # Research overview and intended applications
└── output/       # Generated maps and spatial data when the notebook runs
```
## Running the Notebook
Google Colab is the simplest environment:
1. Open `lab02.ipynb` in Colab.
2. Select **Runtime → Run all**.
3. Allow the notebook to download GADM data.
4. Inspect the maps and generated tables.
5. Download `output/` from the Colab file browser or use the final zipped archive.
Locally, install Jupyter and the required packages:
```bash
pip install jupyter geopandas pyogrio shapely matplotlib pandas numpy requests
jupyter notebook lab02.ipynb
```
An internet connection is required for the GADM downloads.
## Core Technologies
- Python
- GeoPandas
- Pandas and NumPy
- Shapely
- Pyogrio
- Matplotlib
- GADM administrative boundary data
## Research Interpretation
The notebook demonstrates that geospatial research requires more than visualization. Accurate reprojection, explicit coordinate systems, careful geometry handling, and stable formats determine whether an observation can be reproduced or integrated into a larger satellite pipeline.
It also provides a practical bridge between GIS and remote sensing: vector boundaries define **where** to investigate, while future raster observations reveal **what changed, when it changed, and how its impact varies across space**.
