Project 4 - West Nile Virus Prediction
---
    Qi-Wen | Song Yuan | Eng Seng | Jin


#### Problem Statement
---
West Nile virus (WNV) is the leading cause of mosquito-borne disease in the continental United States. It is most commonly spread to people by the bite of an infected mosquito.([CDC, 2020](https://www.cdc.gov/westnile/index.html)). It is a single-stranded RNA virus from the family Flaviviridae, which also contains the Zika, dengue, and yellow fever virus. But unlike the other mosquito-borne diseases above, birds are the primary hosts for the disease and mosquitoes becomes infected by biting these infected birds. Humans who are infected with WNV do not develop high enough levels of virus in their bloodstream and therefore cannot pass the virus onto other biting mosquitoes([CDC, 2018](https://www.cdc.gov/westnile/resources/pdfs/13_240124_west_nile_lifecycle_birds_plainlanguage_508.pdf)).

Infected mosquitos then spread WNV to people and another animals by biting them. Cases of WNV occur during mosquito season, which starts in the summer and continues through fall ([CDC, 2009](https://www.cdc.gov/westnile/index.html)). The main vector mosquito species that is known to spread the disease come from the Culex species, namely Culex pipiens, commonly found in Eastern US, Culex tarsalis found mainly in the Midwest and West US; and finaly Culex quinquefasciatus found in southeastern region of US ([VDCI, 2020](http://www.vdci.net/vector-borne-diseases/west-nile-virus-education-and-mosquito-management-to-protect-public-health#:~:text=West%20Nile%20virus%20is%20spread,feed%20from%20evening%20to%20morning.)).  

While WNV is not extremely virulent and only about 1 in 5 people who are infected develop West Nile fever and other symptoms, about 1 out of every 150 infected develop a serious and sometimes fatal illness ([CDC, 2009](https://www.cdc.gov/westnile/index.html)). There is currently no vaccine against WNV.

In view of the 2002 outbreak of WNV in Chicago, the Chicago Department of Public Health (CDPH) has set up a surveillance and control system to trap mosquitos and test for the presence of WNV. The goal of this project is to use these surveillance data to predict the occurrence of WNV given time, location, and mosquito species.  Findings from this project will guide and inform decisions on where and when to deploy pesticides throughout the city, to maximise pesticide effectiveness and minimise spending.

#### Executive Summary
---
This is a Kaggle challenge and we were given 9 files in total which contained the main datasets (train.csv & test.csv) that recorded that number of mosquitoes found in traps set up for mosquito survelliance, spray data of spray efforts of the City of Chicago in 2011 and 2013, weather data from two weather stations in Chicago and map data from Open Streetmap to aid with visualisations.

The task was to build a binary classification model which would accurately predict the presence of the West Nile Virus when given the test datasets. One of the first challenges we faced as a group was to address the null values that were prevalent in the Weather Data, some missing values were imputed from the other Weather Station as there were two Weather Stations within the City, and some weather metrics (SnowFall) that were not relevant to the Mosquito season were dropped. We also accounted for seasonality of the weather by imputing of Wetbulb, StnPressure and Sealevel with Median with the median value of the month. For the train dataset, we concentrated on dropping the Address Accuracy column as we felt that Address infotypes were sufficient to compare against the test datasets for the location of traps along with creating a new column to measure the total number of mosquitoes per trap for that day as every 50 mosquitoes found in the trap sample for that day creates a new entry in the train dataset. As for the spray dataset, we found that the column Time had too many duplicates and null values to justify keeping and so it was dropped.

In order for us to account for weather conditions on the day that the traps were assessed by the CDPH, we merged the train and weather datasets on the Date columns and used only one set of weather data from the nearest weather station to the relevant trap on the train dataset. With our Exploratory Data Analysis, we were interested in looking at patterns that would be strongly correlated to a positive West Nile Virus diagnosis of a mosquito found in those traps. We found less than 500 of the over 8000 samples contained the West Nile Virus and the number of positive cases did not gradually decrease with the spraying efforts. And so, we were interested in examine any seasonal trends that might be prevalent in the number of mosquitoes and which species might be more susceptible to WNV. Our findings showed that the warmer months in the year brought a seasonal increase in the number of mosquitoes and a seasonal decrease in the cooler months and that the spraying efforts were not having the intended effect on the mosquitoes populations which led us to observing that spraying did take place at traps where most WNV positive cases were found.

With this understanding of the impact of spraying, we looked at the weather data to determine more granular weather metrics that would help us in feature engineering for our classification model. Given the disparity between positive and negative cases of mosquitoes having WNV in the target variable, we employed SMOTE oversampling to oversample the datasets. We employed a variety of models to find the best kaggle score and predict the presence of WNV most accurately.

We also looked into the Cost Benefit analysis of spraying and Vector Control in general to help the CDPH make an informed decision on allocation of resources to combat this virus that has costs the US almost 778 million USD in healthcare and lost productivity costs.


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

#### Cost Benefit Analysis
##### Benefit: Medical Expenses & Lost Productivity
- In Chicago, [there were 49 cases in 2016](https://www.chicago.gov/content/dam/city/depts/cdph/food_env/general/West_Nile_Virus/2016_CDPHArbovirusreport_Final_3162017.pdf), which would have cost **\\$702k** (49 / 906 * \\$12.977 million) in medical expenses and lost productivity. Should there be no spraying done, the number of cases may have been higher.


##### Cost: Spraying
- According to Chicago Department of Public Health, spraying is done using trucks that dispenses an ultra-low-volume spray. [The chemical used is Zenivex E4, applied at a rate of 1.5 fluid ounces per acre.](https://chicago.cbslocal.com/2017/08/30/spray-mosquitoes-far-south-side-west-nile-prevention/)


- Zenivex E4 - [128 fluid ounces costs \\$78.85 (before rebates)](http://www.centralmosquitocontrol.com/-/media/files/centralmosquitocontrol-na/us/resources-lit%20files/2015%20zenivex%20pricing%20brochure.pdf). Costs \\$0.924 per acre if applied at 1.5 fluid ounces.


- Chicago city: 606.1 km² or 148510 acres.
    * Worst case scenario, cost of spraying the whole Chicago city (excluding costs such as manpower, overtime, etc.) = **\\$137k**


**Medical Expenses & Lost Productivity costs incurred is 5 times more expensive than spraying. There are also other costs such as quality of life, tourism and entertainment which have not been accounted for.**

#### Conclusions & Recommendations
Our final model, XGBoost (coupled with SMOTE) achieved a public Kaggle score of 0.697.

##### Key Findings:

1. Mosquito numbers follow the natural onset of the seasons and the data collection for mosquitoes in traps begin in May and stop around October. The presence of the WNV in mosquitoes in those traps usually peak in August and taper off, decreasing to zero as mosquitoes die off or go into hibernation.

2. The spray operations conducted by the City of Chicago and the Chicago Department of Public Health (CDPH) in 2001 and 2013 did not have a noticeable effect on the number of mosquitoes after as the last sprays for 2011 and 2013 coincided with the end of the mosquito season and did not reduce the mosquitoes population significantly during the peak months of July and August.

3. The spray operations in 2011 and 2013 also missed the trap locations where the most cases of WNV positive mosquitoes were found(the only exception being Trap 002).

4. There is a strong correlation between temperature & precipitation and the number of WNV positive mosquitoes found in traps. Most WNV positive cases have been found when the average temperature was between 71F - 80F, and days where the total precipitation was zero or close to zero. This observation is also supported by this study that looked at the use of temperature to improve [West Nile virus forecasts](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1006047 "West Nile virus forecasts").

##### Recommendations
1. Better spraying regime that is informed by the weather and trap data if CDPH decides to proceed with spraying operations. The CDPH should look into more granular block/street meteorological data to get more accurate locations to target their spraying operations. This should provide a more reliable feedback loop to assess if spraying operations in a particular neighborhood has been effective in addressing the area's adult mosquito population.


2. Concentrate efforts to combat [WNV](https://ij-healthgeographics.biomedcentral.com/articles/10.1186/1476-072X-6-10 "WNV") prone areas in Chicago which tend to fall into the two categories outlined in the article above by educating the community on mosquito preventation measures (especially those who live in housing built before 1960s and are close to sea level) and empowering vector control Mosquito Abatement Districts.
        Inner Suburbs, fairly high income, most housing built in 1940s and 1960s.
        City, Low Income, young, some housing built in 1940s and 1960s

3. More public awareness campaigns: Urging people to minimize exposure by dumping any standing water outside every week, and wearing mosquito repellent and protective clothing. Other steps include changing bird baths weekly, stocking ponds with minnows or goldfish that eat mosquito larvae, and using Bti, a naturally occurring bacterium, sold in stores, that kills mosquito larvae in water.



##### Limitations & Further Research
1. The dataset was imbalanced and we had to generate synthetic samples to balance the dataset.

2. Spraying data was limited to only 2 years with no indication of dosage or other information of the spraying regime.

3. Due to computational power limitations, we had only tuned limited combinations of hyperparameters, and may have missed some other combinations.

4. Other mosquito control efforts have not been accounted for in our model to determine the actual effectiveness of spraying.

5. For a more complete analysis of economical costs, data in terms of healthcare expenses and mosquito control efforts related to WNV should be made publicly available.
