# Project 2 - Ames Housing Data and Kaggle Challenge



## Problem Statement



Challenge: You are tasked with creating a regression model based on the Ames Housing Dataset. This model will predict the price of a house at sale in Ames, Iowa United States.



The class was provided with a training dataset (train.csv) and test dataset (test.csv). The training dataset includes the target variable (sale price). We were assigned the challenge of generating a regression model using the training data, predicting values for the target using the test data, and submitting our predictions to the private Kaggle competition for the class to be scored against the actual target values. The preliminary scores given during the competition are based on only 30% of the test data. At the conclusion of the competition, the final submissions are scored against the remaining 70% of the test data. (This is to discourage overfitting the model to the data used for preliminary scores.)



## Presentation Prompt



Presentation Prompt:

You've been recently hired at Zillow and your first work assignment is to build a model that will make the best possible prediction of home values in Ames, Iowa (They reserve the more exciting cities for seasoned veterans, this is your opportunity to prove yoursel!). You will be making a presentation to Zillow's semi-technical staff about the process that led you to your final model and predictions.



Some recommendations of what to include: compelling visuals, significant insights uncovered, noteable obstacles, description of the dataset, the most informative features, interpret coefficients, any features you engineered, any outside data used, description of scaling or regularization if used, any hyperparameter tuning, final model performance.



## My Process



### Data cleaning and EDA

In the data cleaning stage, I did not remove any features in the beginning to avoid in order to keep the data as complete as possible. However, there were a lot of null values in both data sets which required to be fill up or impute with a value.

Checking data type: The following columns have numeric values but data is categorical:



- MS SubClass (Nominal): Identifies the type of dwelling involved in the sale.
- Mo Sold (Discrete): Month Sold (MM) (unique values 1-12)
- Yr Sold (Discrete): Year Sold (YYYY) (unique values: 2006, 2007, 2008, 2009, 2010)



I converted these columns into strings so they could be used to create dummy columns with the other categorical columns later.



Missing values: I checked for null values by column. Columns with a high percentage of null values (higher than 45% null) were removed. Columns removed: 'Pool QC', 'Misc Feature', 'Alley', 'Fence', 'Fireplace Qu'. Remaining null values were assigned to 0 for numeric data and 'na' for strings. This is not the best method of imputing missing values. A future improvement to the project I would like to try would be filling values with the median/most common value for that column.



### Preprocessing and Modeling



Interaction Terms: 

I had created total bath which include the full bath, half bath, basement full bath and basement half bath to increase the correlation of the feature to the price. Next the basement area, which I summed up basement finish 1 and 2 and unfinished area.



After that i dropped the related columns to avoid collinearity which will affect the prediction accuracy. 



The training data was split 95%/5% using scikit-learn train_test_split for cross-validation. Data was scaled using scikit-learn StandardScaler. A future improvement to the project would be to try taking the log of the target variable before fitting the model, as was pointed out in other presentations that the sale price distribution is skewed. (The final predictions would then have to be exponentiated to get the correct values.)



In the beginning, I tried the fasted and dirty ways to create the model by selecting the top 5 correlated features without any interaction done, the Kaggle score is 28,710.62 with RidgeCV model. However this project required us to go thru the workflow so I tested and evaluated models using linear regression, lasso, and ridge algorithms based on the model features. After adding dummy columns, linear regression began predicting negative values for sale price. Lasso and ridge did not have this problem.



| Data & Model      | R^2 score | Kaggle score (RMSE) |
| ----------------- | --------- | ------------------- |
| LassoCV           | 0.8595    | 38915.66            |
| Linear Regression | -1.6189   | -                   |
| RidgeCV           | 0.8332    | -                   |



## Conclusion

The overall quality is the feature that most correlated to sale price which we can suggest that it is add the most value to a house, other than quality the correlations plot suggest that the ground living area is the feature that be add value to a house.

In order to get the house value added, it is suggested that the house owner do remodeling or renovation to renew the outlook of the house, and do periodical maintenance for each feature to make sure the features are in good condition which will be a plus point for the buyer.

Seems Bluestem and Bloomington neighborhood made a good investment which having low sales but the housing price is high comparing to other neighborhood..

There is space of improvement, the data cleaning can be done will filling with median or most common value. RFE will be a model which is good to help us narrow down the features with high correlation and hence, increase the accuracy of prediction prices.
