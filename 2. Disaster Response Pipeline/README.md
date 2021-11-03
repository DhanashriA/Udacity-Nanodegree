# Disaster Response Pipeline Project

 
# Project Overview
In this project, I have applied my data engineering skills to analyze disaster data from [Figure Eight](https://appen.com/) to build a model for an API that classifies disaster messages. I have created a machine learning pipeline to categorize real messages that were sent during disaster events so that the messages could be sent to an appropriate disaster relief agency. 
Along side ETL pipeline and ML pipeline, the project also includes a web app where an emergency worker can input a new message and get classification results in several categories. The web app will also display visualizations of the data.

## Components
There are three components for this project. 

### 1. ETL Pipeline
A Python script, `process_data.py`, writes a ETL pipeline that:

 - Loads the messages and categories datasets
 - Cleans the data
 - Stores it in SQLite database
 
 
### 2. ML Pipeline
A Python script, `train_classifier.py`, writes a machine learning pipeline that:

 - Loads data from the SQLite database
 - Splits the dataset into training and test sets
 - Builds a text processing and machine learning pipeline
  (I have tried these classifiers : Adaboost, GradientBoosting and Randomforest classifier). Out of these Randomforest gave a better accuracy)
 - Improve model using GridSearchCV
 - Exports the final model as a pickle file
 
A jupyter notebook `ML Pipeline Preparation` was used to prepare the train_classifier.py python script. 

### 3. Flask Web App
The project includes a web app where an emergency worker can input a new message and get classification results in several categories. 

## Repository has the following file structure:
- app 
- | - template
- | |- master.html # main page of web app 
- | |- go.html # classification result page of web app
- |- run.py # Flask file that runs app
- data 
- |- disaster_categories.csv # data to process
- |- disaster_messages.csv # data to process
- |- process_data.py
- |- DisasterResponse.db # database to save clean data to
- models
- |- train_classifier.py
- |- classifier.pkl # saved model
- README.md

### Instructions of How to run the Project:
1. Run the following commands in the project's root directory to set up your database and model.

    - To run ETL pipeline that cleans data and stores in database
        `python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/DisasterResponse.db`
    - To run ML pipeline that trains classifier and saves
        `python models/train_classifier.py data/DisasterResponse.db models/classifier.pkl`

2. Run the following command in the app's directory to run your web app.
    `python run.py`

3. Go to http://0.0.0.0:3001/

