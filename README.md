# Berlin PLR Data
Hassle free access to Berlin data, ready to go csv tabular datasets (geometry available for those who want to plot maps). Get deep insights into socio-economic and related data about Berlin's neighborhoods based on actual numbers. Maybe, you're a Berlin resident yourself and you want to explore your surroundings from a data driven perspective? This is where you will find the right datasets and tools!  
This repository contains various preprocessed datasets related to Berlin, with a specific focus on the city's PLRs (Planungsräume = planning spaces).
As of 2021, Berlin monitors social and demographic changes by dividing the city into 542 of said spaces.
Each space is called a Planungsraum (PLR) and features a mean resident count of approximately 7,000. The following figure shows Berlin with its 542 PLRs:  
![Berlin with its 542 PLRs](auxiliary/plr.png)  
--> Each row in the preprocessed datasets corresponds to one of these PLRs. The columns correspond to per PLR features, such as unemployment rate, energy consumption, number of schools, etc...  
--> PLRs are the finest granular spaces of a hierarchical system that is called LOR (lebensweltlich orientierte Räume = lifeworld oriented spaces) which is in detail described [here](https://www.berlin.de/sen/sbw/stadtdaten/stadtwissen/sozialraumorientierte-planungsgrundlagen/lebensweltlich-orientierte-raeume/).  
--> PLRs (LOR in general) are in use since before 2021, but beware, the system was reorganized in 2021. So, pre 2021 PLR datasets have a different total PLR count (447) and different geometry per PLR. This is nothing you have to worry about with the datasets you'll find here. 

**Attention:** Each PLR has its unique ID (column `PLR_ID` in all the datasets). Also, each PLR has a name (column `PLR_NAME` in the datasets), and within the names there is a duplicate ("Schloßstraße"). This is not a mistake, there simply are two different PLRs with the same name. So, do not merge datasets based on `PLR_NAME`, always **merge on `PLR_ID` when combining datasets**!

## Datasets
- Addresses / Adressen: All addresses in Berlin with their respective PLR (no PLR granularity). Can be used for finding an address' PLR.
- Pharmacy Locations / Apothekenstandorte: All pharmacies in Berlin per PLR
- Land ownership / Eigentumskonzentration: Who (natural persons, cooperatives, ...) owns land, not who owns apartments per PLR.
- Charging stations / Elektro-Ladesäulen: Number of electrical charging stations and max power output per PLR.
- Energy consumption / Energieverbrauch: Electrical, district heating, and gas power consumption. Two datasets: per block and per PLR
- Youth centers / Jugendfreizeiteinrichtungen: Youth centers per PLR, count, names, carriers
- Day nurseries / Kitas: Daycare facilities per PLR. Two datasets: simple and verbose
- Violent delinquencies / Monitoring Gewaltdelinquenz: overall violence, youth violence, domestic and partnership per PLR. Two datasets, simplified and regular.
- Social urban development / Monitoring soziale Stadtentwicklung: 3 datasets on social urban development per PLR. Definitely checkout the dataset's [readme](data/monitoring_soziale_stadtentwicklung_2021/README.md), or get directly started using `mss_2021_easy.csv` which is somewhat self explanatory.
- Care facilities / Pflegeeinrichtungen: Care facilities per PLR, contains names, carriers etc...
- PLR: geojson (read with geopandas), containing PLRs with their respective geometry. Used e.g. for plotting heatmaps.
- Schools / Schulen: Schools per PLR, contains names, types, carriers etc...


## Fundamentals and Getting Started
- Datasets are already preprocessed and ready to go.
- Datasets are easy to use, follow a clear structure, and aren't particularly big (542 rows -> number of PLRs).
- The preprocessed (csv-)files do not contain geometry data -> no need for fancy libraries (non programmer friendly).
- Basic structure of the datasets (**read in `PLR_ID` as string, so you don't lose the leading zeros**):  
  `df = pd.read_csv(".../mss_2021_easy.csv", dtype={"PLR_ID": str})`
    | PLR_NAME          |   PLR_ID |   Resident Count |   Unemployment Percent |   Social Benefits Receivers Percent |... |
    |:------------------|---------:|-----------------:|-----------------------:|------------------------------------:|---:|
    | Stülerstraße      | 01100101 |             3419 |                4.22 |                             8.04 |... |
    | Großer Tiergarten | 01100102 |             1791 |                1.15 |                             3.46 |... |
    | Lützowstraße      | 01100103 |             5211 |                5.31 |                            15.52 |... |
    | ...     | ... |             ... |                ...  |                             ... |... |
- Each dataset features `PLR_ID` column with unique values. This column can be used as a key for merging multiple datasets if needed (do not merge on `PLR_NAME` because of the duplicate "Schloßstraße").
- If you want to plot maps, read in e.g. `data/plr/plr_only.geojson` as GeoPandas dataframe. This datasets contains the geometry of each PLR. Merge with your "regular" Pandas dataframe on `PLR_ID`.  
  --> now you have the respective PLR geometry attached to each row.
- Also, you can **checkout Leon Ostermann's [Geodata Berlin](https://github.com/Lucky-0ne/geodata_berlin) repository**, it's a small Python package, which simplifies handling Berlin geometry and spatial datasets a lot (and so much more).

These basic principles are illustrated in the [example_simple](example_simple.ipynb) Jupyter notebook (view online [here](https://nbviewer.org/github/tesch-ch/berlin_PLR_data/blob/main/example_simple.ipynb) with working interactive maps).
There we merge datasets, create a heatmap and an interactive map, showcasing multiple features. All of this with just very few lines of code:  
![heatmap unemployment](auxiliary/heatmap_unemployment.png)
![interactive map gif](auxiliary/animation_cropped.gif)


## How and Where Were the Raw Datasets Obtained?
The source datasets were obtained from [daten.berlin.de](https://daten.berlin.de/) or [FIS-Broker](https://fbinter.stadt-berlin.de/fb/) respectively. Data often WFS...
Have a look at the readme in the dataset's respective directory for specific details and links.  
How did it work in detail?
https://lab.technologiestiftung-berlin.de/projects/fisbroker-to-qgis/en/

## TODOs
- link example to nbviewer https://nbviewer.org/
- Create master dataset, that is a merge of all the plr granularity CSVs
- proper translation of data directories?
- completely translate all features?