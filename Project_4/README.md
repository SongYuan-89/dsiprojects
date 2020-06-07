Project 4 - West Nile Virus Prediction
---
    Qi-Wen | Song Yuan | Eng Seng | Jin

#### Executive Summary
---
West Nile virus (WNV) is the leading cause of mosquito-borne disease in the continental United States. It is most commonly spread to people by the bite of an infected mosquito.([CDC, 2020](https://www.cdc.gov/westnile/index.html)). It is a single-stranded RNA virus from the family Flaviviridae, which also contains the Zika, dengue, and yellow fever virus. But unlike the other mosquito-borne diseases above, birds are the primary hosts for the disease and mosquitoes becomes infected by biting these infected birds. Humans who are infected with WNV do not develop high enough levels of virus in their bloodstream and therefore cannot pass the virus onto other biting mosquitoes([CDC, 2018](https://www.cdc.gov/westnile/resources/pdfs/13_240124_west_nile_lifecycle_birds_plainlanguage_508.pdf)).

Infected mosquitos then spread WNV to people and another animals by biting them. Cases of WNV occur during mosquito season, which starts in the summer and continues through fall ([CDC, 2009](https://www.cdc.gov/westnile/index.html)). The main vector mosquito species that is known to spread the disease come from the Culex species, namely Culex pipiens, commonly found in Eastern US, Culex tarsalis found mainly in the Midwest and West US; and finaly Culex quinquefasciatus found in southeastern region of US ([VDCI, 2020](http://www.vdci.net/vector-borne-diseases/west-nile-virus-education-and-mosquito-management-to-protect-public-health#:~:text=West%20Nile%20virus%20is%20spread,feed%20from%20evening%20to%20morning.)).  

While WNV is not extremely virulent and only about 1 in 5 people who are infected develop West Nile fever and other symptoms, about 1 out of every 150 infected develop a serious and sometimes fatal illness ([CDC, 2009](https://www.cdc.gov/westnile/index.html)). There is currently no vaccine against WNV.

In view of the 2002 outbreak of WNV in Chicago, the Chicago Department of Public Health (CDPH) has set up a surveillance and control system to trap mosquitos and test for the presence of WNV. The goal of this project is to use these surveillance data to predict the occurrence of WNV given time, location, and mosquito species.  Findings from this project will guide and inform decisions on where and when to deploy pesticides throughout the city, to maximise pesticide effectiveness and minimise spending.

#### Folder Organisation:
---
    |__ code
    |   |__ 01 Weather Data Cleaning.ipynb   
    |   |__ 02 Train, Test, Spray Data Cleaning.ipynb
    |   |__ 03 Merging, EDAs.ipynb
    |   |__ 04 Pre-processing and modelling.ipynb
    |__ datasets
    |   |__ mapdata_copyright_openstreetmap_contributors.rds
    |   |__ mapdata_copyright_openstreetmap_contributors.txt
    |   |__ noaa_weather_qclcd_documentation.pdf
    |   |__ spray.csv
    |   |__ spray_clean.csv
    |   |__ submission_ab.csv
    |   |__ submission_dt.csv
    |   |__ submission_lr.csv
    |   |__ submission_rf.csv
    |   |__ submission_xg.csv
    |   |__ test.csv
    |   |__ test_clean.csv
    |   |__ test_weather.csv
    |   |__ train.csv
    |   |__ train_clean.csv
    |   |__ train_weather.csv
    |   |__ weather.csv
    |   |__ weather_clean.csv
    |__ group_presentation.ppt
    |__ README.md

#### Data Dictionary
---

|Feature|Type|Dataset|Description|Comments
|---|---|---|---|---|
|Id            |int      |train.csv/test.csv |ID number of the record|
|Date           |datetime      |train.csv/test.csv |date the WNV test is performed|
|Address      |datetime |train.csv/test.csv| approximate trap address; sent to GeoCoder|
|Species         |str      |train.csv/test.csv| mosquito species in trap|
|Block         |str      |train.csv/test.csv| block number of address|
|Street        |str      |train.csv/test.csv| street of address|
|Trap          |str    |train.csv/test.csv| ID number of the trap|
|AddressNumberAndStreet|str|train.csv/test.csv| approximate address retrieved from GeoCoder|
|Latitude            |float|train.csv/test.csv| latitude retrieved from GeoCoder|
|Longitude            |float|train.csv/test.csv| longitude retrieved from GeoCoder|
|AddressAccuracy      |int|train.csv/test.csv| accuracy of information returned from GeoCoder|
|NumMosquitos        |int      |train.csv/test.csv| number of mosquitoes in a sample|
|WnvPresent           |int      |train.csv/test.csv| whether or not WNV is present in a sample (1 = present; 0 = absent)|
|Date |datetime |spray.csv| date of spray
|Time         |datetime      |spray.csv| time of spray
|Latitude|float|spray.csv| latitude of spray
|Longitude        |float|spray.csv| longitude of spray
|Station  |int|weather.csv| weather station (1 or 2)
|Date     |datetime|weather.csv| date of measurement
|Tmax     |int|weather.csv| maximum daily temperature (F)
|Tmin     |int|weather.csv| minimum daily temperature (F)
|Tavg  |int|weather.csv| average daily temperature (F)
|Depart     |int|weather.csv| departure from normal temperature (F)
|Dewpoint    |int|weather.csv| average dewpoint (F)
|WetBulb  |int|weather.csv| average wet bulb
|Heat     |int|weather.csv| heating degree days
|Cool  |int|weather.csv| cooling degree days
|Sunrise     |int|weather.csv| time of sunrise (calculated)
|Sunset     |int|weather.csv| time of sunset (calculated)
|CodeSum     |str|weather.csv| code of weather phenomena
|Depth     |int|weather.csv| unknown |dropped, too many missing values
|Water1  |int|weather.csv| unknown |dropped, too many missing values
|SnowFall     |int|weather.csv| snowfall (inch) |dropped, snowfall not expected in the observed months
|PrecipTotal     |str|intweather.csv| total daily rainfall (inch)
|StnPressure     |int|weather.csv| average atmospheric pressure (inch Hg)
|SeaLevel     |int|weather.csv| average sea level pressure (inch Hg)
|ResultSpeed  |float|weather.csv| resultant wind speed (mph)
|ResultDir     |int|weather.csv| resultant wind direction (degrees)
|AvgSpeed     |int|weather.csv| average wind speed (mph)

#### Model Evaluation
---
|Model|Kaggle Private|Kaggle Public|
|---|---|---|
|XGBoost |0.68208 |0.69746 |
|AdaBoost |0.54633 |0.54817 |
|Random Forest |0.57653 |0.58826 |
|Decision Tree |0.55050 |0.58735 |
|Log Regression with liblinear solver |0.50735 |0.50228 |
|Log Regression with lbfgs solver |0.50719 | 0.50228 |
