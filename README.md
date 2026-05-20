# Wildfires in Canada
SDS210 course project

## Project Overview
This project analyzes wildfire activity in Canada for the time period 2014 - 2023.
The analysis focuses on wildfire frequency and percentage of burnt area for each province and territory.

### Research Question
How have the number of wildfires in Canada changed between the period 2014 - 2018 and 2019 - 2023, and how have burnt areas across provinces and territories of Canada changed between 2014 and 2023?

## Data
### Sources
The raw open data used in this project:

|Description|Source|URL|Information|
|---|---|---|---|
|Wildfire data of Canada|Government of Canada|[Link Wildfire data](https://cwfis.cfs.nrcan.gc.ca/en/catalogue/results/7355c08f-1590-41cc-a751-8856afaa5959)| Used file: National Fire Database - All Years - CSV|
|Provinces and Territories of Canada|Government of Canada|[Link Province & Territories data](https://www12.statcan.gc.ca/census-recensement/2021/geo/sip-pis/boundary-limites/index2021-eng.cfm?Year=21)|Boundary file options: Language - English, Type - Cartographic Boundary Files (CBF), Administrative boundaries - Provinces/territories, Format - Shapefile (.shp)|

### Storage
- `data/raw/` contains the original downloaded datasets
- `data/processed/` contains the processed data
- `data/processed/wildfire_map/` contains the data needed for the ineractive point map
- `data/processed/choropleth_map/` contains the data needed for the interactive choropleth map

### Coordinate Reference System (CRS)
The original Provinces and Territories of Canada data is provided in EPSG:3347.

The Wildfire data of Canada uses geographic coordinates (latitude and longitude) in EPSG:4326.

To ensure spatial compatibility between datasets
and enable interactive web mapping with Folium, the Provinces and Territories of Canada data has to be
reprojected to EPSG:4326.

## Outputs

### Visible outputs
This project will generate:
- Wildfire frequency histograms for the time period 2014 - 2018 and 2019 - 2023
- Static wildfire maps for the time period 2014 - 2018 and 2019 - 2023 showing where the fires are located and what size they have
- Interactive wildfire maps for the time period 2014 - 2018 and 2019 - 2023 showing where the fires are located and what size they have
- Interactive choropleth map for the years 2014 and 2023 showing how much percentage of each province and territory was burnt

Exported maps and figures are stored in `outputs/`

### Data outputs

|name of file|Inforamtion|Place of storage|
|---|---|---|---|
|fire_clean.csv|Cleaned wildfire data|`data/processed/`|
|fire_14_23.csv|Cleaned wildfire data for the years 2014 - 2023|`data/processed/`|
|canada_4326.gpkg|Provinces and Territories of Canada data with crs EPSG:4326|`data/processed/`|
|fire_tot.scv|Cleaned wildfire data for 2014 - 2023 including a column with size|`data/processed/`|
|wildfire_14_18.csv|Wildfire data for the year 2014 - 2018|`data/processed/wildfire_map/`|
|wildfire_19_23.csv|Wildfire data for the year 2019 - 2023|`data/processed/wildfire_map/`|
|canada_provinces.gpkg|Provinces and Territories of Canada data with crs EPSG:3347, but column "PRENAME" now as "province"|`data/processed/choropleth_map/`|
|burn_area.csv|Wildfire data including for each year and each province the area of the province (in hectare), the area burnt down by wildfire (in hectare) and the percentage of the area burnt down by wildfires|`data/processed/wildfire_map/`| 

## Setup Instructions
### Requirements
- Anaconda
- Python 3.13.11

### Required libraries
```bash
conda install pandas
conda install geopandas
conda install shapely
conda install folium
conda install matplotlib
```
### Running the Project
1. Open Anaconda Prompt
2. Navigate to the project folder
```bash
cd path/to/project/Wildfire
```
3. Start JupyterLab
```bash
jupyter lab
```
## Execution Order
The notebooks have to be run in the following order:
1. `data_cleaning.ipynb`
2. `classes_histograms.ipynb`
3. `interactive_map.ipynb`
4. `area.ipynb`
5. `choropleth_map.ipynb`
