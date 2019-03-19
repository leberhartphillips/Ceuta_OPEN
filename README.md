# Ceuta OPEN
## An open access database of snowy plover breeding ecology
#### Luke J. Eberhart-Phillips, Medardo Cruz-López, and Clemens Küpper

In this repository you can find all the raw data we have collected from >1,300 individually marked snowy plovers (_Charadrius nivosus_) monitored between 2006 and 2012 at Bahía de Ceuta – an important breeding site in western Mexico.

Here

**`Ceuta_OPEN.sqlite`** contains the SQL (Structured Query Language) database of the following 5 tables:

  A. **`Nests`** – a table of all nests found and monitored. Columns are defined as:
  1.	`species`: species of plover (all snowy plover in this case)
  2.	`population`: population at which the data were collected (all Ceuta in this case)
  3.	`year`: year during which the data were collected
  4.	`site`: site at which the data were collected
  5.	`nest`: the ID for a given nest (unique within year and within site)
  6.	`ID`: a concatonation of `year`, `site`, and `nest` to make a unique value
  7.	`easting`: UTM easting
  8.	`northing`: UTM northing
  9.	`utm`: UTM zone
  10.	`found_date`: date nest was initially discovered (mdd format)
  11.	`found_time`: time nest was initially discovered (24h format)
  12.	`laying_date`: date nest is estimated to have been laid based on egg floatation scores (`float1`, `float2`, and `float3`)
  13.	`end_date`: date nest ended (cause specified in `fate`)
  14.	`last_observation_alive`: date nest was last observed active
  15.	`fate`: fate of the nest (e.g., hatched, predated, abandoned, etc.)
  16.	`male`: ring ID of the male seen tending the nest
  17.	`female`: ring ID of the female seen tending the nest
  18.	`no_chicks`: number of chicks hatched from the nest
  19.	`clutch_size`: number of eggs in the nest
  20.	`length1`: length in mm of egg #1
  21.	`width1`: width in mm of egg #1  
  22.	`float1`: float score of egg #1 as defined on page 5 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus")
  23.	`length2`: length in millimeters of egg #2
  24.	`width2`: width in millimeters of egg #2
  25.	`float2`: float score of egg #2 as defined on page 5 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus")
  26.	`length3`: length in millimeters of egg #3
  27.	`width3`: width in millimeters of egg #3
  28.	`float3`: float score of egg #3 as defined on page 5 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus")
  29.	`photo`: indication of if a photo of the nest was taken (1) or not (0)
  30.	`observer`: initials of observer collecting the data
  31.	`comments`: miscellaneous comments pertinent to the nest's observation

  B. **`Broods`** – a table of all broods found and monitored. Columns are defined as:
  1.	`species`: species of plover (all snowy plover in this case)
  2.	`population`: population at which the data were collected (all Ceuta in this case)
  3.	`year`: year during which the data were collected
  4.	`site`: site at which the data were collected
  5.	`brood`: the ID for a given brood (unique within year and within site). Broods originating from known nests retain the ID found in the **`Nests`** table, whereas broods hatching from unknown nests have a negative ID (e.g., `-2`)
  6.	`ID`: a concatonation of `year`, `site`, and `brood` to make a unique value
  7.	`easting`: UTM easting
  8.	`northing`: UTM northing
  9.	`utm`: UTM zone
  10.	`date`: date brood observation was made (mdd format)
  11.	`time`: time brood observation was made (24h format)
  12.	`distance`: estimated distance in meters between brood and observer
  13.	`degree`: estimated bearing of the brood relative to the observer (i.e., the number of degrees in the angle measured in a clockwise direction from the north line to the line joining the observer to the brood)
  14.	`parents`: 
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