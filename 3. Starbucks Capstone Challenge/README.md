# Starbucks Capstone Challenge
## Project Overview
The Starbucks Udacity Data Scientist Nanodegree Capstone challenge data set is a simulation of customer behaviour on the Starbucks rewards mobile application. Periodically, Starbucks sends offers to users that may be an advertisement, discount, or buy one get on free (BOGO). An important characteristic regarding this dataset is that not all users receive the same offer.
This data set contains three files. The first file describes the characteristics of each offer, including its duration and the amount a customer needs to spend to complete it (difficulty). The second file contains customer demographic data including their age, gender, income, and when they created an account on the Starbucks rewards mobile application. The third file describes customer purchases and when they received, viewed, and completed an offer. An offer is only successful when a customer both views an offer and meets or exceeds its difficulty within the offer's duration.

## DATASETS

The data is contained in three files:

* portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
* profile.json - demographic data for each customer
* transcript.json - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

**portfolio.json**
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

**profile.json**
* age (int) - age of the customer
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

**transcript.json**
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record

## Problem Statement / Metrics
The business case that I chose to solve is to build a model that predicts whether a customer will respond to an offer based on the customers demographics and the offers attributes.

## Strategy
Clean and combine the offer portfolio, customer profile, and transaction data. Each row of this combined dataset will describe an offer's attributes, customer demographic data, and whether the offer was successful.
Build the machine learning models and assess the accuracy and F1-score of the models that assumes all offers were successful. Accuracy measures how well a model correctly predicts whether an offer is successful. However, if the percentage of successful or unsuccessful offers is very low, accuracy is not a good measure of a model performance. For this situation, evaluating a models' precision and recall provides better insight to its performance. F1-score metric is a good measure as it's a weighted average of the precision and recall metrics.
Compare the performance of the various machine learning models. 
Refine the parameters of the model that has the highest accuracy and F1-score.

I have built random forest, gradient boosting and catboost models.

Both random forest and gradient boosting models are a combination of multiple decision trees. A random forest classifier randomly samples the training data with replacement to construct a set of decision trees that are combined using majority voting.
Gradient boosting iteratively constructs a set of decision trees with the goal of reducing the number of misclassified training data samples from the previous iteration. 
Typically, gradient boosting performs better than a random forest classifier. However, gradient boosting may overfit the training data and requires additional effort to tune. A random forest classifier is less prone to overfitting because it constructs decision trees from random training data samples. Also, a random forest classifier's hyperparameters are easier to optimize.

CatBoost is an algorithm for gradient boosting on decision trees. Catboost build one of the most accurate model on whatever dataset you feed it with — requiring minimal data prep. It is a readymade classifier in scikit-learn’s conventions terms. Though I have applied it on the cleaned and transformed dataset using one-hot encoding etc, Catboost would deal with the categorical features automatically and is scalable in nature.

## RESULTS

This analysis suggests that a random forest model has the best training data accuracy and F1-score. 
Refined random forest model hyperparameters using a grid search method has training data accuracy of 0.842 and an F1-score of 0.867
The test data set accuracy of 0.65 and F1-score of 0.706 suggests that the random forest model did not overfit the training data.
Which shows that the model will be able to predict the offer response based on the customer demographics and the offer details and the model is not biased towards one particular result. 

"Feature importance" refers to a numerical value that describes a feature's contribution to building a model that maximizes its evaluation metric. A random forest classifier is an example of a model that estimates feature importance during training. The analysis of the Starbucks Capstone Challenge customer offer effectiveness training data suggests that the top features based on their importance are:

1. Membership days 
2. Customer income
3. Customer age 
4. Offer reward  

Since the top features are associated with a customer's demographics, it may be possible to improve the performance of a random forest model by creating features that describe an offer's success rate as a function of these features. 
These additional features will provide a random forest classifier the opportunity to construct a better decision boundary that separates successful and unsuccessful customer offers.
Also it would be interesting to explore Catboost's capabilities further.

Thus, Starbucks can use the RandomForestClassifier to predict whether a customer will accept a particular offer or not and then decide to whom to send out the particular offer.


## ACKNOWLEDGEMENTS
- Starbucks for the data
- Udacity for the opportunity and guidance

