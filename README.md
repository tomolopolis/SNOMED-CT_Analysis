# SNOMED-CT Analysis
This repository provides notebooks & scripts for the exploration and analysis of SNOMED-CT releases availbe from the NHS Digital TRUD [website](https://isd.digital.nhs.uk/)

## Reproduce a SNOMED-CT MedCAT CDB
We have broken this process down into two stages.

### Download and Parse Soure Data
We supply code to parse the following files:
- [SNOMED-CT UK Release](https://isd.digital.nhs.uk/trud3/user/authenticated/group/0/pack/26): This inlcudes the international and UK specific extended terms.
- [SNOMED-CT UK Drug Extension](https://isd.digital.nhs.uk/trud3/user/authenticated/group/0/pack/26): This includes the UK specific brand names, dosages, manufacturers used in UK wide clinical practise. This is updated more frequently than the core terminology
- [ICD-10 Data Files](https://isd.digital.nhs.uk/trud3/user/authenticated/group/0/pack/28): The UK version of the international classification of disease for clincal coding of diseases, this dataset is mapped to SNOMED-CT codes and can be loaded as further metadata into a MedCAT CDB.
- [OPCS-4 Data Files](https://isd.digital.nhs.uk/trud3/user/authenticated/group/0/pack/10): The OPCS Classification of Interventions and Procedures version 4 is terminolgy for clinical coding of procedures in the NHS. 

The first [notebook](https://github.com/tomolopolis/SNOMED-CT_Analysis/blob/master/Exploring%20a%20SNOMED-CT%20Release.ipynb) for prepares the various release files that have been downloaded to your local disk from NHS TRUD. This will output various files to your disk that will then be used to load into a MedCAT CDB.

The second [notebook](https://github.com/tomolopolis/SNOMED-CT_Analysis/blob/master/Build_SNOMED-CT_CDB.ipynb), loads the parsed files into a MedCAT CDB, please note this can take up to 3 hours to complete. Further training of an example corpora of clinical notes (MIMIC-III text not provided) is then run, and ICD / OPCS data is loaded into the CDB. The final action saves the built and optionall trained CDB to disk. Ready to be used in a MedCAT service instance, MedCATtrainer or in another notebook. 

## Analyse SNOMED-CT Relations

A further supplemantary [notebook][https://github.com/tomolopolis/SNOMED-CT_Analysis/blob/master/SNOMED%20hierarchies.ipynb] is provided that analyses the relation terms in SNOMED-CT and produces various caches of relations for the previously loaded concepts.
