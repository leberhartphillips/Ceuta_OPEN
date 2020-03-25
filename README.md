# CeutaOPEN
## Individual-based field observations of breeding snowy plovers *Charadrius nivosus*
### Version 1.1.0 - March 25, 2020
#### Luke J. Eberhart-Phillips, Medardo Cruz-López, Lydia Lozano-Angulo, Salvador Gómez del Ángel, Wendoly Rojas-Abreu, Marcos Bucio-Pacheco, and Clemens Küpper

[![Ceuta Snowy Plovers](https://lukeeberhartphillips.files.wordpress.com/2019/03/ceuta_open_logo_cut-1.png)](https://www.youtube.com/watch?v=h4OxHZXADA8)

In this repository you can find all the raw data we have collected from 1,647 individually marked snowy plovers (_Charadrius nivosus_) monitored between 2006 and 2016 at [Bahía de Ceuta](https://www.google.com/maps/@23.9197739,-106.9668912,2358m/data=!3m1!1e3 "Google Map Satellite") – an important breeding site in western Mexico.

This repository is also available on the *Open Science Framework* at [DOI 10.17605/OSF.IO/3K4FH](https://osf.io/3k4fh/ "OSF CeutaOPEN repo") and is accompanied by the preprint found here: 

[Eberhart-Phillips, LJ, Cruz-López, M, Lozano-Angulo, L, Gómez del Ángel, S, Rojas-Abreu, W, & Küpper, C. CeutaOPEN: Individual-based field observations of breeding snowy plovers *Charadrius nivosus*. *bioRxiv* 2019.12.20.884825 (2019)](https://www.biorxiv.org/content/10.1101/2019.12.20.884825v1 "bioRxiv manuscript")

When using the database, please cite as:

*Eberhart-Phillips et al (2020). CeutaOPEN v1.1. Open Science Framework. DOI 10.17605/OSF.IO/3K4FH*

#### Repository Contents
**`R/`**

  - [`Ceuta_OPEN.Rmd`](https://github.com/leberhartphillips/Ceuta_OPEN/blob/master/R/Ceuta_OPEN.Rmd "RMarkdown") and [`Ceuta_OPEN.html`](https://github.com/leberhartphillips/Ceuta_OPEN/blob/master/R/Ceuta_OPEN.html "html") contains a detailed commented analytical workflow for utilizing `CetuaOPEN` with the RSQLite and dplyr packages in R.
  

**`data/Ceuta_OPEN_version_releases/`**

  - [`Ceuta_OPEN_v1.sqlite`](https://github.com/leberhartphillips/Ceuta_OPEN/blob/master/data/Ceuta_OPEN_version_releases/Ceuta_OPEN_v1.sqlite "Ceuta OPEN data") contains the SQL (Structured Query Language) database of the following 5 tables (please click the black arrows to see column definitions):

  <details>
  <summary>A. <b><code>Nests</code></b> – a table of all nests found and monitored.</summary>
  
  Columns are defined as:

  1.	`species`: species of plover (all snowy plover 'SNPL' in this case)
  2.	`population`: population at which nest was monitored (all Ceuta in this case)
  3.	`year`: year during which nest was monitored
  4.	`site`: site at which nest was monitored
  5.	`nest`: unique identifier of nest (unique within year and within site)
  6.	`ID`: a concatenation of `year`, `site`, and `nest` to make a unique value across sites and years
  7.	`easting`: UTM easting of nest
  8.	`northing`: UTM northing of nest
  9.	`utm`: UTM zone of nest
  10.	`found_date`: date nest was discovered (stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’)
  11.	`found_time`: time nest was discovered (24h format, e.g., 1633)
  12.	`nest_initiation_date`: estimated date when the first egg of the nest was laid (i.e., its 'initiation'). The estimate is calculated by subtracting the age in days of the oldest egg (determined by the floatation scores`float1`, `float2`, and `float3` defined below) and a 5-day laying period for three-egg clutches or a 3-day laying period for two-egg clutches or a 1-day laying period for one-egg clutches (egg-laying intervals are based on [Page et al. 2009](http://obpa-nc.org/DOI-AdminRecord/0071935-0072002.pdf "Snowy Plover (Charadrius alexandrinus), The Birds of North America Online")). Determining initiation dates of clutches found at stage `F` is imprecise, and thus we estimated the initiation date by subtracting 25 days from the hatch date (i.e., the average length of incubation in this population) and an additional 5, 3, or 1 days for the laying period depending on the clutch size. For nests found at stage `F` that failed before hatching, the nest initiation date is `NA`.
  13.	`end_date`: date nest ended (stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’; cause specified in `fate`)
  14.	`last_observation_alive`: date nest was last observed active (stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’)
  15.	`fate`: fate of nest (either: Abandoned, Flooded, Hatch, Predated, Unhatched, Other, or Unknown)
  16.	`male`: ring ID of male seen tending nest
  17.	`female`: ring ID of female seen tending nest
  18.	`no_chicks`: number of chicks hatched from nest
  19.	`clutch_size`: number of eggs found in nest
  20.	`length1`: length in millimeters of egg #1
  21.	`width1`: width in millimeters of egg #1 
  22.	`float1`: float score of egg #1 as defined on page 5 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus")
  23.	`length2`: length in millimeters of egg #2
  24.	`width2`: width in millimeters of egg #2
  25.	`float2`: float score of egg #2 as defined on page 5 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus")
  26.	`length3`: length in millimeters of egg #3
  27.	`width3`: width in millimeters of egg #3
  28.	`float3`: float score of egg #3 as defined on page 5 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus")
  29.	`photo`: indication if a photo of nest was taken (1) or not (0)
  30.	`observer`: initials of observer who found nest
  31.	`comments`: miscellaneous comments pertinent to nest's observation
  </details>
  
  <details>
  <summary>B. <b><code>Broods</code></b> – a table of all broods found and monitored.</summary>
  
  Columns are defined as:
  
  1.	`species`: species of plover (all snowy plover ‘SNPL’ in this case)
  2.	`population`: population at which brood was observed (all Ceuta in this case)
  3.	`year`: year during which brood was observed
  4.	`site`: site at which brood was observed
  5.	`brood`: unique identifier of brood (unique within year and within site). Broods originating from known nests retain the `nest` identifier found in the **`Nests`** table, whereas broods hatching from unknown nests have a negative identifier (e.g., `-2`)
  6.	`ID`: a concatenation of `year`, `site`, and `nest` to make a unique value across sites and years
  7.	`easting`: UTM easting of brood observation
  8.	`northing`: UTM northing of brood observation
  9.	`utm`: UTM zone of brood observation
  10.	`date`: date brood observation was made (stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’)
  11.	`time`: time brood observation was made (24h format, e.g., 1633)
  12.	`distance`: estimated distance in meters between brood and observer
  13.	`degree`: estimated bearing of brood relative to observer (i.e., the number of degrees in the angle measured in a clockwise direction from the north line to the line joining the observer to the brood)
  14.	`parents`: parents attending brood at time of observation (0 = no parent present; 1 = one parent (not identified whether male or female); 2 = female only (2+ when female certainly identified, whilst male uncertain); 3 = male only (3+, i.e., opposite of 2+); 4 = both present)
  15.	`male`: ring ID of male observed tending brood
  16.	`female`: ring ID of female observed tending brood
  17.	`chicks`: number of chicks observed in brood
  18.	`chick_codes`: color ring combinations of all chicks observed (individuals seperated by a comma). The scheme can be noted as XX.XX|XX.XX where X indicates a color (or metal) ring, the full stop marks the position of 'knee-joint' and the pipe divides the left and right leg. Thus the readout is "left above . left below | right above . right below". See page 9 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus") for more details.
  19.	`photo`: indication if a photo of the brood was taken (1) or not (0)
  20.	`observer`: initials of observer making brood observation
  21.	`comments`: miscellaneous comments pertinent to brood's observation
  </details>

  <details>
  <summary>C. <b><code>Captures</code></b> – a table of all captures made.</summary>
  
  Columns are defined as:
  
  1.	`species`: species of plover (all snowy plover ‘SNPL’ in this case)
  2.	`population`: population at which capture was made (all Ceuta in this case)
  3.	`year`: year during which capture was made
  4.	`site`: site at which capture was made
  5.	`nest`: unique identifier of nest at which capture was made (unique within year and within site). If capture was made at a brood originating from a unknown nest, the ID is negative (e.g., `-2`).
  6.	`ID`: a concatenation of `year`, `site`, and `nest` to make a unique value
  7.	`ring`: alpha-numeric code of metal ring assigned to captured individual
  8.	`code`: color-ring combination assigned to captured individual. The scheme can be noted as XX.XX|XX.XX where X indicates a color (or metal) ring, the full stop marks the position of 'knee-joint' and the pipe divides the left and right leg. Thus the readout is "left above . left below | right above . right below". See page 9 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus") for more details.
  9.	`age`: age of captured individual (J = juvenile (chicks and first-years), A = adult (second years and older))
  10. `field_sex`: sex of individual determined in the field based on ornamentation and other clues (e.g., time of capture, parental care, etc.), where F = female, M = males, and J = unknown sexed juvenile.
  11. `mol_sex`: sex of individual determined in the lab with the P2/P8 and Calex-31 markers (for our PCR conditions see [dos Remedios et al. (2015)](https://onlinelibrary.wiley.com/doi/full/10.1111/ibi.12263 "Ontogenic differences in sexual size dimorphism across four plover populations")), where F = female, M = males, U = insufficient molecular evidence (e.g., markers failed), and NA = individual not molecularly sex-typed. Note: All birds initially captured in years after 2013 have not yet been molecularly sex-typed.
  12.	`sex`: sex of captured individual (F = female, M = males, J = unknown sexed juvenile)
  13.	`easting`: UTM easting of capture
  14.	`northing`: UTM northing of capture
  15.	`utm`: UTM zone of capture
  16.	`date`: date capture was made (%Y-%m-%d POSIX format, e.g., 2008-05-14)
  17.	`time`: time capture was made (24h format, e.g., 1633)
  18.	`parents`: parents attending captured individual (if `age` = "J") at time of observation (0 = no parent present; 1 = one parent (not identified whether male or female); 2 = female only (2+ when female certainly identified, whilst male uncertain); 3 = male only (3+, i.e., opposite of 2+); 4 = both present)
  19.	`weight`: weight in grams of captured individual
  20.	`bill`: length in millimeters of upper mandible of captured individual. Measured as the distance between the tip of the forehead feathering at the base of the upper bill, along the ridge of the culmen, and the tip of the bill (also known as the "exposed culmen" measurement; _sensu_ page 8 of Pyle, P. 1997. Identification guide to North American birds. Part 1, Columbidae to Ploceidae. State Creek Press, Bolinas, CA)
  21.	`left_tarsus`: length in millimeters of left tarsus of captured individual. Measured as the distance between the notch at the end of the lateral condyle of the tibiotarsus on the backside of the leg, to the last tarsal scute on the front of the leg at the base of the foot (also known as the "outside tarsus" or "diagonal tarsus" measurement; _sensu_ page 11 of Pyle, P. 1997. Identification guide to North American birds. Part 1, Columbidae to Ploceidae. State Creek Press, Bolinas, CA)
  22.	`right_tarsus`: same as `left_tarsus` measurement above but for right leg of captured individual
  23.	`left_wing`: length in millimeters of left wing of captured individual. Measured as the distance from the carpal joint (the bend of the wing) to the longest primary feather whilst flattening the wing and straightening the primaries (also known as the "maximum flat" or "flattened and straightened" measurement; _sensu_ page 6 of Pyle, P. 1997. Identification guide to North American birds. Part 1, Columbidae to Ploceidae. State Creek Press, Bolinas, CA)
  24.	`right_wing`: same as `left_wing` measurement above but for right wing of captured individual
  25.	`blood`: indication if blood from captured individual was collected (1) or not (0)
  26.	`moult`: primary molt score of captured individual. Scored as a the stage of the moult and the number of feathers at that stage. See [Ringers' Manual, British Trust for Ornithology, Thetford](https://www.bto.org/sites/default/files/u17/downloads/about/resources/primary-moult.pdf "Moult Scoring") for more details.
  27.	`fat`: fat score of captured individual, scored as the amount of visible fat in the furcular region or tracheal pit. See [Ringers' Manual, British Trust for Ornithology, Thetford](https://www.bto.org/sites/default/files/u17/downloads/about/resources/Fat%20score.pdf "Fat Scores") for more details.
  28.	`lice`: indication if feather lice from captured individual were collected (1) or not (0)
  29.	`fecal`: indication if faeces from captured individual was collected (1) or not (0)
  30.	`photo`: indication if a photo of captured individual was taken (1) or not (0)
  31.	`observer`: initials of observer making capture
  32.	`comments`: miscellaneous comments pertinent to capture event
  </details>

  <details>
  <summary>D. <b><code>Resights</code></b> – a table of all resightings of color-marked individuals.</summary>
  
  Columns are defined as:
  
  1.	`species`: species of plover (all snowy plover ‘SNPL’ in this case)
  2.	`population`: population at which resighting was made (all Ceuta in this case)
  3.	`year`: year during which resighting was made
  4.	`site`: site at which resighting was made
  5.	`easting`: UTM easting of observer's location while resighting
  6.	`northing`: UTM northing of observer's location while resighting
  7.	`utm`: UTM zone of observer's location while resighting
  8.	`date`: date resighting was made (stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’)
  9.	`time`: time resighting was made (24h format, e.g., 1633)
  10.	`distance`: estimated distance in meters between resighted bird and observer
  11.	`degree`: estimated bearing of resighted bird relative to the observer (i.e., the number of degrees in the angle measured in a clockwise direction from the north line to the line joining the observer to the brood)
  12.	`code`: color-ring combination of the resighted individual. The scheme can be noted as XX.XX|XX.XX where X indicates a color (or metal) ring, the full stop marks the position of 'knee-joint' and the pipe divides the left and right leg. Thus the readout is "left above . left below | right above . right below". See page 9 of [Székely, Kosztolányi, and Küpper (2008)](https://www.researchgate.net/publication/228494424_Practical_guide_for_investigating_breeding_ecology_of_Kentish_plover_Charadrius_alexandrinus "Practical guide for investigating breeding ecology of Kentish plover Charadrius alexandrinus") for more details.
  13.	`sex`: sex of individual determined in the field based on ornamentation and other clues (e.g., capture history, parental care, etc.), where F = female, M = males, and J = unknown sexed juvenile
  14.	`census`: indication if the resighting was conducted as part of a census count (1) or not (0)
  15.	`observer`: initials of observer making resighting
  16.	`comments`: miscellaneous comments pertinent to the resighting
  </details>
  
  <details>
  <summary>E. <b><code>BirdRef</code></b> – a table of all families monitored and the identification of their members.</summary>

  Columns are defined as:
  
  1.	`species`: species of plover (all snowy plover ‘SNPL’ in this case)
  2.	`population`: population at which family was observed (all Ceuta in this case)
  3.	`year`: year during which family was observed
  4.	`site`: site at which family was observed
  5.	`family`: unique identified of family (unique within year and within site). Families found as a nests retain `nest` ID found in **`Nests`** table, whereas families found as broods hatching from unknown nests have a negative `brood` ID (e.g., `-2`) found in **`Broods`** table)
  6.	`ID`: a concatenation of `year`, `site`, and `nest` to make a unique value across all sites and years
  7.	`nest_initiation_date`: estimated date when the first egg of the nest was laid (i.e., its 'initiation'). The estimate is calculated by subtracting the age in days of the oldest egg (determined by the floatation scores`float1`, `float2`, and `float3` defined above in the `Nests` table) and a 5-day laying period for three-egg clutches or a 3-day laying period for two-egg clutches or a 1-day laying period for one-egg clutches (egg-laying intervals are based on [Page et al. 2009](http://obpa-nc.org/DOI-AdminRecord/0071935-0072002.pdf "Snowy Plover (Charadrius alexandrinus), The Birds of North America Online")). Determining initiation dates of clutches found at stage `F` is imprecise, and thus we estimated the intiation date by subtracting 25 days from the hatch date (i.e., the average length of incubation in this population) and an additional 5, 3, or 1 days for the laying period depending on the clutch size. For nests found at stage `F` that failed before hatching, the nest initiation date is `NA`. Stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’
  8.	`hatching_date`: date nest hatched (stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’; "NA" if nest `fate` was other than "Hatch" in **`Nests`** table)
  9.	`male`: ring ID of male parent observed with nest/brood
  10.	`female`: ring ID of female parent observed with nest/brood
  11.	`chick1`: ring ID of first chick seen in brood
  12.	`chick2`: ring ID of second chick seen in brood
  13.	`chick3`: ring ID of third chick seen in brood
  14.	`exp`: indication if family was part of an experiment
  15.	`type`: indication of type of experiement conducted
  16.	`manip`: date of the experimental manipulation (stored in the internal `Date` format of R and represents the number of days since January 1, 1970, the ‘Unix epoch’. Converted easily in R using ‘as.Date(x, origin = “1970-01-01”)’)
  </details>
  
#### Terms of Use

The CeutaOPEN database shall be used in accordance with the Creative Commons Attribution 4.0 International Public License (see [**`license.txt`**](https://github.com/leberhartphillips/Ceuta_OPEN/blob/master/license.txt "Terms of Use") for more details). For all projects making considerable use of the `CeutaOPEN` database, it is encouraged that users reach out to Luke Eberhart-Phillips (luke.eberhart[at]orn.mpg.de) or Clemens Küpper (ckuepper[at]orn.mpg.de) to offer the opportunity to comment prior to the publication of the work.