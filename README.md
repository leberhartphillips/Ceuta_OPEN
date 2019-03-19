# Ceuta OPEN
## An open access database of snowy plover breeding ecology
#### Luke J. Eberhart-Phillips, Medardo Cruz-López, Clemens Küpper

In this repository you can find all the raw data we have collected from >1,300 individually marked snowy plovers (_Charadrius nivosus_) monitored between 2006 and 2012 at Bahía de Ceuta – an important breeding site in western Mexico.

**`Ceuta_OPEN.sqlite`** contains the SQL (Structured Query Language) database of the following 5 tables:

  A. **`Nests`** – a table of all nests found and monitored. Columns are defined as:
  1.	`species`: species of plover ()
  2.	`population`
  3.	`year`
  4.	`site`
  5.	`nest`
  6.	`ID`
  7.	`easting`
  8.	`northing`
  9.	`utm`
  10.	`found_date`
  11.	`found_time`
  12.	`laying_date`
  13.	`end_date`
  14.	`last_observation_alive`
  15.	`fate`
  16.	`male`
  17.	`female`
  18.	`no_chicks`
  19.	`clutch_size`
  20.	`length1`
  21.	`width1`  
  22.	`float1`
  23.	`length2`
  24.	`width2`
  25.	`float2`
  26.	`length3`
  27.	`width3`
  28.	`float3`
  29.	`photo`
  30.	`observer`
  31.	`comments`

  B. **`Broods`** – a table of all broods found and monitored. Columns are defined as:
  1.	`species`
  2.	`population`
  3.	`year`
  4.	`site`
  5.	`brood`
  6.	`ID`
  7.	`easting`
  8.	`northing`
  9.	`utm`
  10.	`date`
  11.	`time`
  12.	`distance`
  13.	`degree`
  14.	`parents`
  15.	`male`
  16.	`female`
  17.	`chicks`
  18.	`chick_codes`
  19.	`brood_photo`
  20.	`observer`
  21.	`comments`

  C. **`Captures`** – a table of all captures made. Columns are defined as:
  1.	`species`
  2.	`population`
  3.	`year`
  4.	`site`
  5.	`nest`
  6.	`ID`
  7.	`ring`
  8.	`code`
  9.	`age`
  10.	`sex`
  11.	`easting`
  12.	`northing`
  13.	`utm`
  14.	`date`
  15.	`time`
  16.	`parents`
  17.	`weight`
  18.	`bill`
  19.	`left_tarsus`
  20.	`right_tarsus`
  21.	`left_wing`
  22.	`right_wing`
  23.	`blood`
  24.	`moult`
  25.	`fat`
  26.	`lice`
  27.	`fecal`
  28.	`photo`
  29.	`observer`
  30.	`comments`

  D. **`Resights`** – a table of all resightings of color-marked individuals. Columns are defined as:
  1.	`species`
  2.	`population`
  3.	`year`
  4.	`site`
  5.	`easting`
  6.	`northing`
  7.	`utm`
  8.	`date`
  9.	`time`
  10.	`distance`
  11.	`degree`
  12.	`code`
  13.	`sex`
  14.	`census`
  15.	`observer`
  16.	`comments`

  E. **`BirdRef`** – a table of all families monitored and the identification of their members. Columns are defined as:
  1.	`species`
  2.	`population`
  3.	`year`
  4.	`site`
  5.	`nest`
  6.	`ID`
  7.	`laying_date`
  8.	`hatching_date`
  9.	`male`
  10.	`female`
  11.	`chick1`
  12.	`chick2`
  13.	`chick3`
  14.	`exp`
  15.	`type`
  16.	`manip`