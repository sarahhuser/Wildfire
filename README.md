# Wildfires in Canada
University of Zurich, SDS210 course project

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
|Wildfire data of Canada|Government of Canada|[Link Wildfire data](https://cwfis.cfs.nrcan.gc.ca/geoserver/wfs?service=WFS&version=1.1.0&request=GetFeature&outputFormat=csv&typeNames=public:NFDB_point&sortBy=REP_DATE+D)| Used file: National Fire Database - All Years - CSV|
|Provinces and Territories of Canada|Government of Canada|[Link Province & Territories data](https://www12.statcan.gc.ca/census-recensement/2021/geo/sip-pis/boundary-limites/files-fichiers/lpr_000b21a_e.zip)|Boundary file options: Language - English, Type - Cartographic Boundary Files (CBF), Administrative boundaries - Provinces/territories, Format - Shapefile (.shp)|

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

## Project Structure
```bash
Wildfire/
|-- README.md
|--  data/
|   |-- raw/                         # Original, unmodified data
|   |   |--  NFDB_point.csv
|   |   |__ lpr_000b21a_e.zip
|   |__ processed/                   # Processed data
|       |--  choropleth_map/
|       |     |-- burnt_area-csv
|       |     |__ canada_provinces.gpkg
|       |--  wildfire_map/
|       |     |--  wildfire_14_18.csv
|       |     |__ wildfire_19_23.csv
|       |--  canada_4326.gpkg
|       |--  fire_12_23.csv
|       |--  fire_clean.csv
|       |__  fire_tot.csv
|-- notebook/
|   |--  data_cleaning.ipynb
|   |--  classes_histograms.ipynb
|   |--  interactive_map.ipynb
|   |--  area.ipynb
|   |__  choropleth_map.ipynb
|-- outputs/
|   |--  histogram_2014_2018.png
|   |--  histogram_2019_2023.png
|   |--  static_map_2014_2018
|   |--  static_map_2019_2023
|   |-- interactive_map.html
|   |__ choropleth_map.html
|__ environment.yml
```

## Outputs

### Visible outputs
This project will generate:
- Wildfire frequency histograms for the time period 2014 - 2018 and 2019 - 2023
- Optional: Static wildfire maps for the time period 2014 - 2018 and 2019 - 2023 showing where the fires are located and what size they have
- Interactive wildfire maps for the time period 2014 - 2018 and 2019 - 2023 showing where the fires are located and what size they have
- Interactive choropleth map for the years 2014 and 2023 showing how much percentage of each province and territory was burnt

Exported maps and figures are stored in `outputs/`

### Data outputs

|Name of file|Information|Place of storage|
|---|---|---|
|fire_clean.csv|Cleaned wildfire data|`data/processed/`|
|fire_14_23.csv|Cleaned wildfire data for the years 2014 - 2023|`data/processed/`|
|canada_4326.gpkg|Provinces and Territories of Canada data with crs EPSG:4326|`data/processed/`|
|fire_tot.scv|Cleaned wildfire data for 2014 - 2023 including a column with size|`data/processed/`|
|wildfire_14_18.csv|Wildfire data for the year 2014 - 2018 including a column with size|`data/processed/wildfire_map/`|
|wildfire_19_23.csv|Wildfire data for the year 2019 - 2023 including a column with size|`data/processed/wildfire_map/`|
|canada_provinces.gpkg|Provinces and Territories of Canada data with crs EPSG:3347, but column "PRENAME" now as "province"|`data/processed/choropleth_map/`|
|burn_area.csv|Wildfire data including for each year and each province the area of the province (in hectare), the area burnt down by wildfire (in hectare) and the percentage of the area burnt down by wildfires|`data/processed/wildfire_map/`| 

## Setup Instructions
### Step 1: Clone repository
```bash
git clone https://github.com/sarahhuser/Wildfire.git
cd Wildfire
```
### Step 2: Create and activate the environment
```bash
conda env create -f environment.yml
conda activate sds210-wildfire
```
In the environment.yml the all required packages for this project are installed:
- jupyter lab
- pandas
- geopandas
- matplotlib
- shapely
- folium
- jenkspy 

### Step: Open jupyter lab
```bash
jupyter lab
```

### Step 4: Raw data storage
After downloading the raw data, as described in the table of the section data > soures, make sure to store the files in the `data/raw` folder. It is important that for the Provinces and Territories of Canada data the whole zip is stored in the raw folder!
Furthermore, make sure that your repository looks the same as in the section Project Structure!

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
