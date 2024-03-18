# berlin_PLR_data
This repository contains various preprocessed datasets about the city of Berlin focused on the spatial granularity of PLR (Planungsraum).
The source datasets were obtained from [daten.berlin.de](https://daten.berlin.de/) or [FIS-Broker](https://fbinter.stadt-berlin.de/fb/) respectively.  

## List of Datasets
- Addresses / Adressen: All addresses in Berlin with their respective PLR
- Pharmacy Locations / Apothekenstandorte: All pharmacies in Berlin per PLR
- Land ownership / Eigentumskonzentration: Who (natural persons, cooperatives, ...) owns land, not who owns apartments per plr.
- Charging stations / Elektro-Ladesäulen: Number of electrical charging stations and max power output per plr.
- Energy consumption / Energieverbrauch: Electrical, district heating, and gas power consumption. Two datasets: per block and per PLR
- Youth centers / Jugendfreizeiteinrichtungen: Youth centers per plr, count, names, carriers
- Day nurseries / Kitas: Daycare facilities per PLR. Two datasets: simple and verbose
- Violent delinquencies / Monitoring Gewaltdelinquenz: overall violence, youth violence, domestic and partnership per PLR. Two datasets, simplified and regular.
- Social urban development / Monitoring soziale Stadtentwicklung: 3 datasets on social urban development per plr. Definitely checkout the dataset's [readme](data/monitoring_soziale_stadtentwicklung_2021/README.md), or get directly started using `mss_2021_easy.csv` which is somewhat self explanatory.
- Care facilities / Pflegeeinrichtungen: Care facilities per PLR, contains names, carriers etc...
- PLR:
- Schools / Schulen: Schools per PLR, contains names, types, carriers etc...


## Structure of the Datasets
All of the preprocessed datasets follow this structure represented by an excerpt of the dataset [mss_2021_easy.csv](data/monitoring_soziale_stadtentwicklung_2021/mss_2021_easy.csv):
| PLR_NAME          |   PLR_ID |   Resident Count |   Unemployment Percent |   Social Benefits Receivers Percent |   Child Poverty Percent |   ... |
|:------------------|---------:|-----------------:|-----------------------:|------------------------------------:|------------------------:|-------------------------:|
| Stülerstraße      | 01100101 |             3419 |                4.22594 |                             8.04329 |                19.398   |                  ... |
| Großer Tiergarten | 01100102 |             1791 |                1.15858 |                             3.46175 |                 8.33333 |                  ... |
| Lützowstraße      | 01100103 |             5211 |                5.31544 |                            15.5249  |                32.6316  |                  ... |
| Körnerstraße      | 01100104 |             4636 |                6.18102 |                            18.0112  |                39.9399  |                  ... |
| Wilhelmstraße     | 01100205 |             2573 |                2.8826  |                             6.33502 |                19.7581  |                  ... |
- The columns ``PLR_NAME`` and ``PLR_ID`` are part of every PLR dataset



[Here](data/README.md) you can find a more in detail description of the datasets