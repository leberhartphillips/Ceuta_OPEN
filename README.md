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
  6.	`ID`: a concatenation of `year`, `site`, and `nest` to make a unique value
  7.	`easting`: UTM easting
  8.	`northing`: UTM northing
  9.	`utm`: UTM zone
  10.	`found_date`: date nest was initially discovered (mdd format)
  11.	`found_time`: time nest was initially discovered (24h format)
  12.	`laying_date`: date nest is estimated to have been laid based on egg floatation scores (`float1`, `float2`, and `float3`)
  13.	`end_date`: date nest ended (mdd format; cause specified in `fate`)
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
  5.	`brood`: ID for a given brood (unique within year and within site). Broods originating from known nests retain the ID found in the **`Nests`** table, whereas broods hatching from unknown nests have a negative ID (e.g., `-2`)
  6.	`ID`: a concatenation of `year`, `site`, and `brood` to make a unique value
  7.	`easting`: UTM easting
  8.	`northing`: UTM northing
  9.	`utm`: UTM zone
  10.	`date`: date brood observation was made (mdd format)
  11.	`time`: time brood observation was made (24h format)
  12.	`distance`: estimated distance in meters between brood and observer
  13.	`degree`: estimated bearing of the brood relative to the observer (i.e., the number of degrees in the angle measured in a clockwise direction from the north line to the line joining the observer to the brood)
  14.	`parents`: parents attending the brood at the time of observation (0 = no parent present; 1 = one parent (not identified whether male or female); 2 = female only (2+ would be female certainly identified, male unclear); 3 = male only (3+, the opposite of 2+); 4 = both present)
  15.	`male`: ring ID of the male seen tending the brood
  16.	`female`: ring ID of the female seen tending the brood
  17.	`chicks`: number of chicks seen in the brood
  18.	`chick_codes`: color ring combinations of all chicks seen (individuals seperated by a comma). The scheme can be noted as XX.XX|XX.XX where X indicates a color (or metal) ring, the full stop marks the position of 'knee-joint' and the pipe divides the left and right leg. Thus the readout is "left above . left below | right above . right below". See page 9 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus") for more details.
  19.	`photo`: indication of if a photo of the brood was taken (1) or not (0)
  20.	`observer`: initials of observer collecting the data
  21.	`comments`: miscellaneous comments pertinent to the brood's observation

  C. **`Captures`** – a table of all captures made. Columns are defined as:
  1.	`species`: species of plover captured (all snowy plover in this case)
  2.	`population`: population at which the capture was made (all Ceuta in this case)
  3.	`year`: year during which the capture was made
  4.	`site`: site at which the capture was made
  5.	`nest`: ID of the nest at which the capture was made (unique within year and within site). If the capture was made at a brood originating from a unknown nest, the ID is negative (e.g., `-2`).
  6.	`ID`: a concatenation of `year`, `site`, and `nest` to make a unique value
  7.	`ring`: alpha-numeric code of the metal ring assigned to the captured individual
  8.	`code`: color-ring combination assigned to the captured individual. The scheme can be noted as XX.XX|XX.XX where X indicates a color (or metal) ring, the full stop marks the position of 'knee-joint' and the pipe divides the left and right leg. Thus the readout is "left above . left below | right above . right below". See page 9 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus") for more details.
  9.	`age`: age of the captured individual (J = juvenile (chicks and first-years), A = adult (second years and older))
  10.	`sex`: sex of the captured individual (F = female, M = males, J = unknown sexed juvenile)
  11.	`easting`: UTM easting
  12.	`northing`: UTM northing
  13.	`utm`: UTM zone
  14.	`date`: date brood observation was made (mdd format)
  15.	`time`: time brood observation was made (24h format)
  16.	`parents`: parents attending the captured individual (if `age` = "J") at the time of observation (0 = no parent present; 1 = one parent (not identified whether male or female); 2 = female only (2+ would be female certainly identified, male unclear); 3 = male only (3+, the opposite of 2+); 4 = both present)
  17.	`weight`: weight in grams of captured individual
  18.	`bill`: length in millimeters of upper mandible of captured individual. Measured as the distance between the tip of the forehead feathering at the base of the upper bill, along the ridge of the culmen, and the tip of the bill (also known as the "exposed culmen" measurement; _sensu_ page 8 of Pyle, P. 1997. Identification guide to North American birds. Part 1, Columbidae to Ploceidae. State Creek Press, Bolinas, CA)
  19.	`left_tarsus`: length in millimeters of the left tarsus of captured individual. Measured as the distance between the notch at the end of the lateral condyle of the tibiotarsus on the backside of the leg, to the last tarsal scute on the front of the leg at the base of the foot (also known as the "outside tarsus" or "diagonal tarsus" measurement; _sensu_ page 11 of Pyle, P. 1997. Identification guide to North American birds. Part 1, Columbidae to Ploceidae. State Creek Press, Bolinas, CA)
  20.	`right_tarsus`: same as `left_tarsus` measurement above but for right leg of captured individual
  21.	`left_wing`: length in millimeters of the left wing of captured individual. Measured as the distance from the carpal joint (the bed of the wing) to the longest primary feather whilst flattening the wing and straightening the primaries (also known as the "maximum flat" or "flattened and straightened" measurement; _sensu_ page 6 of Pyle, P. 1997. Identification guide to North American birds. Part 1, Columbidae to Ploceidae. State Creek Press, Bolinas, CA)
  22.	`right_wing`: same as `left_wing` measurement above but for right wing of captured individual
  23.	`blood`: indication if blood from the captured individual was collected (1) or not (0)
  24.	`moult`: primary molt score of the captured individual. Scored as a the stage of the moult and the number of feathers at that stage. See [Ringers' Manual, British Trust for Ornithology, Thetford](https://www.bto.org/sites/default/files/u17/downloads/about/resources/primary-moult.pdf "Moult Scoring") for more details.
  25.	`fat`: fat score of the captured individual, scored as the amount of visible fat in the furcular region or tracheal pit. See [Ringers' Manual, British Trust for Ornithology, Thetford](https://www.bto.org/sites/default/files/u17/downloads/about/resources/Fat%20score.pdf "Fat Scores") for more details.
  26.	`lice`: indication if feather lice from the captured individual were collected (1) or not (0)
  27.	`fecal`: indication if faeces from the captured individual was collected (1) or not (0)
  28.	`photo`: indication if a photo of the captured individual was taken (1) or not (0)
  29.	`observer`: initials of observer collecting the data
  30.	`comments`: miscellaneous comments pertinent to the capture

  D. **`Resights`** – a table of all resightings of color-marked individuals. Columns are defined as:
  1.	`species`: species of plover (all snowy plover in this case)
  2.	`population`: population at which the data were collected (all Ceuta in this case)
  3.	`year`: year during which the data were collected
  4.	`site`: site at which the data were collected
  5.	`easting`: UTM easting
  6.	`northing`: UTM northing
  7.	`utm`: UTM zone
  8.	`date`: date brood observation was made (mdd format)
  9.	`time`: time brood observation was made (24h format)
  10.	`distance`: estimated distance in meters between brood and observer
  11.	`degree`: estimated bearing of the brood relative to the observer (i.e., the number of degrees in the angle measured in a clockwise direction from the north line to the line joining the observer to the brood)
  12.	`code`: color-ring combination of the resighted individual. The scheme can be noted as XX.XX|XX.XX where X indicates a color (or metal) ring, the full stop marks the position of 'knee-joint' and the pipe divides the left and right leg. Thus the readout is "left above . left below | right above . right below". See page 9 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus") for more details.
  13.	`sex`: sex of the resighted individual
  14.	`census`: indication if the resighting was conducted as part of a census count (1) or not (0)
  15.	`observer`: initials of observer collecting the data
  16.	`comments`: miscellaneous comments pertinent to the capture

  E. **`BirdRef`** – a table of all families monitored and the identification of their members. Columns are defined as:
  1.	`species`: species of plover (all snowy plover in this case)
  2.	`population`: population at which the family was observed (all Ceuta in this case)
  3.	`year`: year during which the family was observed
  4.	`site`: site at which the family was observed
  5.	`family`: the ID for a given family, unique within year and within site (families found as a nests retain the `nest` ID found in the **`Nests`** table, whereas families found as broods hatching from unknown nests have a negative `brood` ID (e.g., `-2`) found in the **`Broods`** table)
  6.	`ID`: a concatenation of `year`, `site`, and `nest` to make a unique value across all sites and years
  7.	`laying_date`: date nest is estimated to have been laid based on egg floatation scores (`float1`, `float2`, and `float3`)
  8.	`hatching_date`: date nest hatched (mdd format; "NA" if nest `fate` was other than "HATCH" in **`Nests`** table)
  9.	`male`: ring ID of the male parent observed with the nest/brood
  10.	`female`: ring ID of the female parent observed with the nest/brood
  11.	`chick1`: ring ID of first chick seen in the brood
  12.	`chick2`: ring ID of second chick seen in the brood
  13.	`chick3`: ring ID of third chick seen in the brood
  14.	`exp`: indication if the family was part of an experiment
  15.	`type`: indication of the type of experiement conducted
  16.	`manip`: date of the experimental manipulation (in mdd format)