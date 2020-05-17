# Project 3 - Reddit API Classification & Natural Language Processing



## Problem Statement



In this project, we will explore how well Natural Language Processing Model differentiate post content from two similar subreddits, and which combinations of model and classifier works best? What is the accuracy and how much of the miss-classification will occur between two different subreddit posts.



## Executive Summary

### Contents:

- [01. API Web Scraping - Python](./code/01. API Web Scraping-Python.ipynb#01.-API-Web-Scraping-&-Data-Cleaning---/r/Python)
- [02. API Web Scraping-Bigdata](./code/02. API Web Scraping-Bigdata.ipynb#02.-API-Web-Scraping-&-Data-Cleaning---/r/bigdata)
- [03. EDA, Preprocessing, Modeling & Conclusion](./code/03. EDA, Preprocessing, Modeling & Conclusion.ipynb#03.-EDA,-Pre-Processing,-Modeling-&-Conclusion)



### Data Source

The following links are the source of the data used to classify the subreddits.
r/depression: https://www.reddit.com/r/Python
r/anxiety: https://www.reddit.com/r/bigdata



| Model             | Classifier     | Best Params                                                  | Train score | Test Score | tn   | tp   |   fp | fn   | Accuracy | Miss-classification Rate | Precision | Specificity | Recall |
| ----------------- | -------------- | ------------------------------------------------------------ | ----------- | ---------- | ---- | ---- | ---: | ---- | -------- | ------------------------ | --------- | ----------- | ------ |
| TF-IDF Vectorizer | Multinomial NB | tf____max_df': 0.9, 'tf____max_features': 5000, 'tf____min_df': 3, 'tf____ngram_range': (1, 2) | 0.9258      | 0.8505     | 148  | 165  |   25 | 30   | 0.8505   | 0.1495                   | 0.8684    | 0.8555      | 0.8462 |

### Evaluation

Multinomial Naive Bayes with TfidrVectorizer performs slightly better with a slightly more accurate result with 85%.
2 reasons that the posts might be incorrectly classified:

1. The user might post in the subrredit topic in either one of subreddit, this will happen because both Python and Bigdata subreddit were related topics.
2. The post is related to both topics, so the post can be classified in either subreddit.



### Conclusion

The Random Forest with TfidfVectorizer worked fairly well with an accuracy score of close to 85%, even though both subreddits were fairly similar in nature.
Logistic Regression with TfidfVectorizer also works equally well as well with an accuracy score of 84%
We can expand our scope to include the following to further improve the models:

- Include lemmatization, stemming and spell checks to have a general feel of the posts
- Include more subreddits (eg. bipolar) in our classification model. This may be further extended to be used as an initial diagnosis of any mental issues that the user might be suffering from.
- Tuning of parameters for random forest to get a better score. However, this requires a longer amount of time to tune to get the perfect parameters.
- Consider either boosting or bagging to get a more optimal outcome.