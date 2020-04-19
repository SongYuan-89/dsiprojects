# Project 1: SAT & ACT Analysis

#### Problem Statement

SAT and ACT are two of the most widely acceped standard test used in college in United States. The perceptions is that either student would take certain test to apply for college they intended go. Investigate the correlation among the data for both test in year 2017 and 2018 by study the trends that present in the data.



 #### Structure

- 2017 Data Import & Cleaning  

  - The project begins with import and cleaning the year 2017 data. 

- 2018 Data Import and Cleaning  

  - 2018 data is manually extracted and cleaned using the same process as ye. 

- Data Dictionary for All Data Used

  - Data dictionary of final data of year 2017 and year 2018 to be analyzed.

- Exploratory Data Analysis 

  -  Summary statistics and brief descriptions of data groups and comparisons with each data.

-  Data Visualization

  -  Histograms, scatter plots, and box plots to study data trends.

-  Descriptive and Inferential Statistics 

  - Summarizing distribution of data and apply statistical inference where appropriate. 

-  Outside Research  

  - Identifying promising trends and researching possible underlying reasons, giving 3 states as example.

- Conclusions and Recommendations 

  - Key takeaways and recommendations to increase the participation rate.

    

#### Data Dictionary for All Data Used 

| Feature                | Type   | Dataset | Description                                                  |
| ---------------------- | ------ | ------- | ------------------------------------------------------------ |
| state                  | object | SAT/ACT | The state in which the data collected in America             |
| act_participation_2017 | float  | ACT     | ACT participation rate by state for year 2017                |
| act_english_2017       | float  | ACT     | Mean score of ACT English test for year 2017                 |
| act_math_2017          | float  | ACT     | Mean score of ACT Math test for year 2017                    |
| act_reading_2017       | float  | ACT     | Mean score of ACT Reading test for year 2017                 |
| act_science_2017       | float  | ACT     | Mean score of ACT Science test for year 2017                 |
| act_composite_2017     | float  | ACT     | Mean score of ACT English, Math, Reading & Science for year 2017 |
| sat_participation_2017 | float  | SAT     | SAT participation rate by state for year 2017                |
| sat_erw_2017           | float  | SAT     | Mean score of SAT Evidence-Based Reading & Writing (ERW) test for year 2017 |
| sat_math_2017          | float  | SAT     | Mean score of SAT Math test for year 2017                    |
| sat_total_2017         | float  | SAT     | Mean composite score of SAT ERW and Math test for year 2017  |
| act_participation_2018 | float  | ACT     | ACT participation rate by state for year 2018                |
| act_english_2018       | float  | ACT     | Mean score of ACT English test for year 2018                 |
| act_math_2018          | float  | ACT     | Mean score of ACT Math test for year 2018                    |
| act_reading_2018       | float  | ACT     | Mean score of ACT Reading test for year 2018                 |
| act_science_2018       | float  | ACT     | Mean score of ACT Science test for year 2018                 |
| act_composite_2018     | float  | ACT     | Mean score of ACT English, Math, Reading & Science for year 2018 |
| sat_participation_2018 | float  | SAT     | SAT participation rate by state for year 2018                |
| sat_erw_2018           | float  | SAT     | Mean score of SAT Evidence-Based Reading & Writing (ERW) test for year 2018 |
| sat_math_2018          | float  | SAT     | Mean score of SAT Math test for year 2018                    |
| sat_total_2018         | float  | SAT     | Mean composite score of SAT ERW and Math test for year 2018  |



 ## Conclusions and Recommendations 

**Key Takeaways**<br>

- Based on the data from year 2017 to 2018 for both ACT and SAT,the state education department had made decision to change their education policies and requirement which lead to relative huge changes in ACT and SAT participation rate for each states. From the example of outside research, we also found that implementation of new policies are usually correlated to competition between ACT and SAT by bidding in this case.<br>
- For the case in Colorado and Illinois state, both state's department of education had implemented SAT as their compulsory requirement for all high school student in the state. Which is the fact that contributed to extreme increment in SAT participation rate and nosedive in participation rate of ACT.<br>
- Ohio state had made either ACT or SAT were compulsory for each high school students. This resulted both test participation rate to increase.<br>
- Overall SAT scores improved in year 2018 despite the higher participation rate comparing to previous year, while ACT score remain level.<br>
- The cost of SAT test is relatively high comparing to ACT test which might affect the budget focus administrators.<br>

**Recommendation**<br>
- To target the states which are yet to confirm and review local college admissions provider policies.<br>
- Lower the test cost in order to lighten the lower income family to bear the test cost by introduce waivers or subsidy.<br>
- Create workshops or seminar to increase the student interest on the test and have them well prepared for the test by showcase them the improvement of SAT test year to year.<br>
- Increase the interest of student to take part in the test by engaging local department of education to offer discounted price.<br>

**Conclusion**<br>
In order to have more accurate in investigation, we may look into additional data such as the headcount of the total student participated in the test for each states and that would be interesting to have the university admission criteria for each state which will affect the participation rate for each test.