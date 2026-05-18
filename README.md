# Wildfires in Canada
sds210 project

## Research Question
How have the number of wildfires in Canada changed between the periods 2014 – 2018 and 2019 – 2023, and how have burnt areas across provinces and territories of Canada changed between 2014 and 2023?

## Data Sources

The raw open data used in this project:

|Description|Source|URL|Information|
|---|---|---|---|
|Wildfire data of Canada|Government of Canada|[Link Wildfire data](https://cwfis.cfs.nrcan.gc.ca/en/catalogue/results/7355c08f-1590-41cc-a751-8856afaa5959)| Used file: National Fire Database - All Years - CSV|
|Provinces and Territories of Canada|Government of Canada|[Link Province & Territories data](https://www12.statcan.gc.ca/census-recensement/2021/geo/sip-pis/boundary-limites/index2021-eng.cfm?Year=21)|Boundary file options: Language - English, Type - Cartographic Boundary Files (CBF), Administrative boundaries - Provinces/territories, Format - Shapefile (.shp)| so this should be enough?

## Setup Instructions

### Requirements
- Anaconda
- Python 3.13.11

### Required libraries
```bash
conda install pandas
conda install geopandas
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
