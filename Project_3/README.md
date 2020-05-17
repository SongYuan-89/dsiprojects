# Project 3: Reddit API Classification & Natural Language Processing



## Problem Statement

In this project, we will explore how well Natural Language Processing Model differentiate post content from two similar subreddits, and which combinations of model and classifier works best? What is the accuracy and how much of the miss-classification will occur between two different subreddit posts.

## Executive Summary

### Contents:
- 1. API Web Scraping-Python
- 2. API Web Scraping-Bigdata
- 3. EDA, Preprocessing, Modeling & Conclusion

### Data Source

The following links are the source of the data used to classify the subreddits.
r/depression: https://www.reddit.com/r/Python
r/anxiety: https://www.reddit.com/r/bigdata

### Evaluation

Multinomial Naive Bayes with TfidrVectorizer performs slightly better with a slightly more accurate result.
2 reasons that the posts might be incorrectly classified:

1. The user might post in the subrredit topic in either one of subreddit, this will happen because both Python and Bigdata subreddit were related topics.
2. The post is related to both topics, so the post can be classified in either subreddit.

## Conclusion and Recommendations

- The Multinomial Naive Bayes with Countvectorizer perform well with accuracy score at 87%, even though both subreddits were related. This project can be further improve by expand the scopes to include following steps:
    - Collect more subreddits post from both subreddits topics
    - Not to drop duplicates of the same user id, drop the similar post instead
    - Tuning the parameters of each model to acheive better scores, however this will required a long amount of time for computer to tune and compile the best parameters.
    - Consider others classifiers such as Adaboost, Gradientboost, etc.
    - Stop word to reduce to only 'english', even thought the title of the subreddit will the the word which occur most frequent in the end to lower the overfit of the data.
