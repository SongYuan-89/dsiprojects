# Capstone Project: NBA Player Analysis and Hall Of Famer Predictions

## Problem Statement

For this capstone project, we want to predict which NBA players will have higher probability to get nominated as Hall Of Fame in the near future. By obtaining the datasets which available on Kaggle, we would like to know :

​	1) Which features will have higher correlations for Hall Of Fame predictions / classifications ?
​	2) Feature Engineering required to increase the accuracy of predictions / classifications ?
​	3) Which features to be chosen for the modeling to predict / classify probability for each player

In order to achieve our goal to get the Hall of Fame predictions for the NBA players.

## Executive Summary

### Contents:
- 1. Data Cleaning
- 2. EDA and Feature Engineering
- 3. Modeling, Results and Conclusions

### Data Source

The following link is the source of the data used for NBA player analysis and Hall of Famer Predictions, which was scraped from [Basketball Reference](https://www.basketball-reference.com) until year 2017:
https://www.kaggle.com/drgilermo/nba-players-stats/kernels



### Data Sets

The datasets which obtained from the kaggle link above:

| Data Sets Name | df Name in Notebook | Descriptions                                                 |
| -------------- | ------------------- | ------------------------------------------------------------ |
| Season_stats   | stats               | Data frame shape of 24691 x 53, the season stats recorded each player total performance in that particular season. Refer to the [Basketball Reference Glossary](https://www.basketball-reference.com/about/glossary.html) for the details of each features contained in the data set. |
| player_data    | data                | Data frame shape of 4550 x 9, each players positions, height,weight, birthdate, college,year start and year end were recorded in this data set. |
| players        | player              | Data frame shape of 3921 x 8, each player height, weight, college, year born, birth city, birth state were recorded in this data set. |



### Modeling Analysis with Parameters 

| Models                   | Best Params                                                  | Train Score | Descriptions / Analysis                                      |
| ------------------------ | ------------------------------------------------------------ | ----------- | ------------------------------------------------------------ |
| Random Forest Classifier | 'rf__max_depth': 2, 'rf__max_leaf_nodes': 3, 'rf__min_samples_leaf': 1, 'rf__n_estimators': 10000 | 0.9105      | The train score is lower but the results seems acceptable, but by comparing with XGBoost Classifier model, the probability results is lower. |
| AdaBoost Classifier      | 'ada__learning_rate': 0.7, 'ada__n_estimators': 10000        | 1.0         | Even though the train score is 1.0, but the probability were lower than 0.7 |
| XGBoost Classifier       | 'xg__learning_rate': 0.6                                     | 1.0         | The train score is 1.0 and comparing the results, the probability by XGBoost Classifications seems perform better than other 2 models |



### Evaluation

XGBoost Classifier seems perform better comparing with other 2 classifiers, even though the AdaBoost's train score is same as XGBoost, however the probability results none were higher than 0.7 which is not acceptable. While for Random Forest Classifier, the train score was slightly lower comparing with other 2 classifier, but the probability classification results is acceptable comparing with the AdaBoost worst results, but XGBoost has better results comparing with Random Forest Classifier.

## Conclusion and Recommendations

**Conclusion**

- After EDA done, I had chose 20-22 features for modeling and classifications to predict which NBA players will have higher probabily to be nominated as Hall Of Famer in near future. The train test split was done manually instead of using train_test_split.
  
    - Train data : Players who were retired at 1997 or players who already nominated as Hall Of Famer
    
    - Test data: Players who were still playing after 1997 and not nominated as Hall of Famer yet.
    
- From 3 classification modeling, the XGBoost Model seems perform better comparing to other 2 models, with better accuracy and results.



**Recommendation**

The datasets only recorded until year 2017, so it is good to get the newer datasets to get better results and predictions for the modeling.

