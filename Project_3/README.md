# Project 3: Web APIs & Classification

## Problem Statement

Reddit is a collection of online discussion boards known as "subreddits", which cover a variety of topics. The goal of this project is to classify which subreddit a given post came from. As there are [over 1.5 million subreddits](http://redditmetrics.com/history) on reddit, we will be classifying posts from two subreddits, [/r/personalfinance](https://www.reddit.com/r/personalfinance/) and [/r/relationship_advice](https://www.reddit.com/r/relationship_advice/), to make the project manageable. The choice of these two subreddits is motivated by their text-heavy posts. We will be creating and comparing two models: a logistic regression and a multinomial naive Bayes classifier. Our results may be useful for any reddit user who is unsure which subreddit is the most appropriate to submit his new post, so that he can attract the most comments.

## Executive Summary

### Contents:
- [1. Data Collection](./code/subreddit_classifier.ipynb#1.-Data-Collection)
- [2. Data Cleaning and EDA](./code/subreddit_classifier.ipynb#2.-Data-Cleaning-and-EDA)
- [3. Pre-processing and Modeling](./code/subreddit_classifier.ipynb#3.-Pre-processing-and-Modeling)
- [4. Evaluation and Conceptual Understanding](./code/subreddit_classifier.ipynb#4.-Evaluation-and-Conceptual-Understanding)
- [5. Conclusion and Recommendations](./code/subreddit_classifier.ipynb#5.-Conclusion-and-Recommendations)

## Data Dictionary

Feature|Type|Description
---|---|---
**name**|_object_|Unique id of a post.
**title**|_object_|Title of a post.
**text**|_object_|Body text of a post.
**subreddit**|_object_|Which subreddit the post came from.

## Conclusion and Recommendations

- Our multinomial naive Bayes classifier performed well with a test accuracy score of 98.73%. This is within expectations because the topics of our two chosen subreddits differ significantly.
- [Subreddit Classifier](https://subreddit-classifier.herokuapp.com/) - A proof of concept web application was developed to demonstrate potential use case. Users can submit their draft post in the application to determine which of the two subreddits should the post be submitted to.
- Scope for future improvements:
    - Optimize stop words and explore strategies for stemming and lemmatization
    - Try ensemble models, such as random forest classifier
    - Ability for model to classify more than two subreddits
