# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2: Ames Housing Data & Kaggle Challenge

### OVERVIEW
Property owners who wish to put their property up for sale tend to want to obtain a preliminary valuation for consideration.

As a Data Scientist for a Property-Tech Company in the USA, we are tasked to build the algorithm behind this web app and recommend the optimal number of features to provide a balance between accuracy and user experience (because nobody likes to fill in lengthy forms!). Having this app is also important to attract users to use our online property marketplace and allow us to earn revenue from partnerships & ads.

To ensure that User Experience is optimized, the user is not going to input more than 10 fields in our web app as it would increase the cost of engagement of the user and may result in lower utilisation of our web app.

### PROBLEM STATEMENT

Using the regression models learnt (Linear Regression, Lasso, Ridge, Elastic Net), decide on a regression model that will be deployed in our web app that uses not more than 10 features (which corresponds to 10 fields) within a reasonable RMSE to provide a prediction on a property's selling price.

We will also be providing submissions to Kaggle to score our regression models against unseen data.

### DATASETS & NOTEBOOKS

We will be using the following datasets in the notebooks, brief description of the datasets below:

* [`train.csv`]: Training data for the Ames Housing Dataset
* [`test.csv`]: Test data for the Ames Housing Dataset, without Target Variable.

---

### METHODOLOGY

The methodology is as follows:

* 1 -  Imputation of missing values for ordinal, discrete and continuous features
* 2.2 - Label Encoding of ordinal features, correlation analysis
* 2.2 - Removal of outliers, feature engineering and manual selection of nominal features for model
* 3 - Model using Ordinary Least Squares (OLS) Linear Regression, LASSO & Ridge regression and scored using RMSE
    * Run all 3 regression models and extract top 5/10/15/20/25/30 features at intervals of 5 features for each model
    * Run all 3 regression models again with each feature set (each regression model will be ran with its top 5/10/15/20/25/30 features)
    * Select optimal model for each feature set (e.g. Using only top 5/10/15/20/25/30 features, select the best performing regression model)
    * Submission of best performing model for top 5/10/15/20/25/30 features (Total of 6 submissions to Kaggle)
* 4 - Using Kaggle and Validation during training to select optimal number of features

The data dictionary for the features used in this dataset can be found on the [Kaggle challenge website](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data)

---
### MODEL SELECTION

| Number of Features | Optimal Model | Training RMSE | Kaggle RMSE |
|---|---|---|---|
| 5 | Ridge | 32278 | 30767 |
| 10 | LASSO | 25563 | 110795 |
| 15 | LASSO | 25613 | 78737 |
| 20 | LASSO | 24522 | 56719 |
| 25 | LASSO | 22861 | 45939 |
| 30 | LASSO | 21400 | 45631 |
| 90 (All features) | Ridge | 20,290 | N/A

* From modelling, we observe that the LASSO model achieved better cross-validated RMSE scores than the rest of the models for top 10 features and above, whereas the Ridge regression model performed the best for top 5 features.

* The Ridge regression model using 5 features will serve as our baseline RMSE as we expect the scores to get better as we include more features. As mentioned above, with the exception of the baseline, inclusion of additional features tend to increase the RMSE of the model when exposed to unseen data during submission to Kaggle.

* The model likely does not have an overfitting as it uses relatively few features (max 30/90 features) and the RMSE score, nor is it an underfitting problem as the RMSE score when all 90 features are fitted (approx 20K) is relatively close to the RMSE score with 30 features (approx 21K). Therefore a plausible explanation would be the presence of outliers in the Kaggle test set, which adversely impacted the performance of the regression model.

* Selecting the best performing model against unseen data (5 features) led to a RMSE (taking the kaggle test set) that is approximately 18% (or ~$30K) of the mean SalePrice of the training set, which is acceptable given that the valuation obtained via our web app is supposed to be a preliminary valuation.

Therefore, we will select features = **5** as the number of features in our web app that requires user input. This is in agreement with existing User Experience (UX) literature to keep fields in a form to below 10 fields for optimal user engagement and conversion. The underlying model is the Ridge Regression.
---
### INTERPRETATION OF COEFFICIENTS  

| Feature Names | Coefficient |
|---|---|
| Gr Liv Area | 0.14053 |
| Overall Qual | 0.21168 |
| has_bsmt | -0.27008 |
| Overall Cond | 0.30878 |
| Lot Area | 0.04276 |
|  |  |
|  |  |

* The coefficients of Ridge regression model using the top 5 features is shown in the dataframe below and can be interpreted as such (due to Log1p transformations on the target and the features) instead of a **unit change** of a feature causing constant change in the target, the effect of the features on the target will be in terms of percentages.

**The coefficient can be interpreted as the approximate percent increase in the the target(`SalePrice`) for every 1% increase in the features while holding other features constant.**

For example, this means that a 1% increase in `Gr Liv Area` would result in a ~0.14% increase in the `SalePrice`, holding the other 9 features constant. The largest contributor to `SalePrice` is `Gr Liv Area`.

Note that the strongest coefficients are

### ANSWERING THE BUSINESS QUESTION AND FUTURE WORK

We have selected the Ridge Regression model with 5 features as the most performing model for our web app. The RMSE is approximately $30,000 and is sufficient to provide a preliminary valuation to provide a benchmark for our users in the USA. On our website, the user will be asked to input the following information to feed into our regression model:

- `Gr Liv Area`:Above grade (ground) living area square feet
- `Overall Qual`: Rates the overall quality of the property
- `has_bsmt`: Whether the property has a basement
- `Overall Cond`: Rates the overall material and finish of the property
- `Lot Area`: Lot size in square feet

Having such a low number of features also improves the User Experience as it would not take up too much time to fill in the information required by our app.

The accuracy of the model can be further improved by:

1. Collecting more data from our US cities as certain preferences may be unique to Ames, Iowa. Collecting more samples will allow the model to generalize better to unseen data.

2. There are many hidden features inside the `Neighborhood` feature as many other possible other features characterize whether a property in a particular neighborhood is of value, such as crime rate, proximity to good schools, proximity to employment centers or near rivers/lakes. Such features should be collected instead of stating the neighborhood of the property.
