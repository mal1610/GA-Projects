
![Logo](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/th5xamgrr6se0x5ro4g6.png)


## Authors

- [Malcolm Lau](https://github.com/mal1610)


# Project 3: Web APIs and Natural Language Processing (NLP)


**Deliverable: Binary Classification Model**


Posts were obtained from both each the r/Football
and r/SoccerBetting subreddits to train a binary
classification model to build a binary classification model
that would classify whether a post belonged to r/Football or r/Soccerbetting.
The classification result will be used as a proxy to detect posts that contain
betting/gambling content.



**Background**


Reddit is an American social news aggregation, web content rating, and discussion website. Registered members submit content to the site and the site is organized by subject into user-created boards called "subreddits", which cover a variety of topics such as news, politics, religion, movies, video games, music, books, sports, fitness, cooking, pets, and image-sharing etc. Moderation is also conducted by community-specific moderators, who are not considered Reddit employees.

Due to the laissez-faire approach adopted by Reddit with respect to online content, it is common for inappropriate content such as illegal/undesirable activities to be posted online on Reddit before those posts can be removed by community moderators, which can be a time-consuming and tedious process for larger subreddits.

**Business Problem**


The moderators of the r/Football subreddit (the customer) has engaged our Tech Consultancy firm to develop a classification model to detect whether a post is related to Soccer Betting in the subreddit. The moderators do not wish for gambling content to be on the subreddit as there are users who are minors and such content would not be appropriate. The intent is for the model to be ran periodically to remove soccer-betting related posts from the subreddit.

## Results
Using the [PushShift API](https://github.com/pushshift/api),
2000 posts each were obtained from the r/Football and r/Soccerbetting subreddits. The data was preprocessed, tokenized and provided as input into  the candidate models.


The modelling results are shown below:


| Model | Text Vectorization | Train Score | Test Score | Specificity | Recall | Precision | F1 | AUC |
|---|---|---|---|---|---|---|---|---|
| Multinomial Naive Bayes | TF-IDF Vectorization | 0.972 | 0.913 | 0.867 | 0.948 | 0.875 | 0.925 | 0.966 |
| K Nearest Neighbors | TF-IDF Vectorization | 0.916 | 0.897 | 0.823 | 0.953 | 0.875 | 0.913 | 0.952 |
| Random Forest | TF-IDF Vectorization | 1 | 0.897 | 0.806 | 0.966 | 0.867 | 0.914 | 0.957 |
| Logistic Regression | Count Vectorization | 0.989 | 0.894 | 0.816 | 0.953 | 0.871 | 0.910 | 0.957 |


The best model is the **Multinomial NB/TF-IDF** model as it offered the highest accuracy on the test test, as well as the highest specificity and AUC score among all the other classifiers.
## Conclusion & Future Work


After cleaning and preprocessing the data, several models were fitted and compared to the benchmark model. Using the desired performance metric (accuracy and specificity), the **Multinomial Naive Bayes/TF-IDF Classifier** provided the best results on the test data and was selected as the classifier of choice for production as part of the moderator tools to ensure that gambling content is policed in the r/Football subreddit.

### Suggested Improvements


* **Increase Model Vocabulary**: Instead of simply obtaining data from the r/Soccerbetting subreddit, data can be obtained from other subreddits which centre on gambling in general (such as [r/Gambling](https://www.reddit.com/r/gambling/), this will increase the model's ability to generalize when exposed to more generic words associated with gambling.


* **Improve Data Quality**: One of the likely reasons for misclassification is typo errors from the user (mentioned above), improvements to the text preprocessing function that takes common spelling errors into account would enhance the text preprocessing capability of the model. The `TextBlob` library with the `Word` module is one way to rectify common typo errors. Rectifying spelling mistakes will enable improve lemmatization and stemming performance, which will likely contribute to improvements in model performance.
