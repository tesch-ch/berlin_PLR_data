# Elektro-Ladesäulen Standorte
Number of electrical charging stations for cars per PLR and their combined power output.  
Preprocessing involved assigning points of stations to PLR polygons/geometry, grouping by plr and calculating the combined power output.

- Columns: PLR_ID,PLR_NAME,charging_stations,charging_points,combined_power_kW
- Date: 2023 December
- Berlin Open Data: https://daten.berlin.de/datensaetze/elektro-lades%C3%A4ulen-wfs
- WFS endpoint: https://gdi.berlin.de/services/wfs/eladesaeulen