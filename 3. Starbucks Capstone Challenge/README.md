# Starbucks Capstone Challenge
## Project Overview
The Starbucks Udacity Data Scientist Nanodegree Capstone challenge data set is a simulation of customer behaviour on the Starbucks rewards mobile application. Periodically, Starbucks sends offers to users that may be an advertisement, discount, or buy one get on free (BOGO). An important characteristic regarding this dataset is that not all users receive the same offer.
This data set contains three files. The first file describes the characteristics of each offer, including its duration and the amount a customer needs to spend to complete it (difficulty). The second file contains customer demographic data including their age, gender, income, and when they created an account on the Starbucks rewards mobile application. The third file describes customer purchases and when they received, viewed, and completed an offer. An offer is only successful when a customer both views an offer and meets or exceeds its difficulty within the offer's duration.

## Datasets

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

## Problem Statement
The business case that I chose to solve is to build a classifier that predicts whether a customer will respond to an offer based on the customers demographics and the offers attributes.

## Dependencies : None

## Installations 
- from sklearn.preprocessing import MultiLabelBinarizer
- import datetime
- from sklearn import metrics
- from tqdm import tqdm
- from sklearn.model_selection import train_test_split
- from sklearn.ensemble import GradientBoostingClassifier, RandomForestClassifier
- from sklearn.model_selection import RandomizedSearchCV
- from sklearn.metrics import accuracy_score, f1_score
- import matplotlib.pyplot as plt
- import seaborn as sns
- import re
- import warnings
- warnings.filterwarnings('ignore')
- from sklearn.datasets import make_classification
- from sklearn.neighbors import KNeighborsClassifier
- from sklearn.inspection import permutation_importance

### Code
Starbucks_Capstone_notebook.IPYNB 

### Link to my Blog
https://medium.com/@dsjoshi24/starbucks-capstone-project-f0d1add1da10


