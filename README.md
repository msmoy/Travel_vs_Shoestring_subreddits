# Subreddit Post Predictions
--------

## Table of Contents:

* [Introduction](#introduction)
* [Technologies](#technologies)
* [Data Description](#data-description)
* [Modeling Process Overview](#modeling-process-overview)
* [Project Status](#project-status)
* [Contributing](#contributing)
* [Source](#source)

---
### Introduction:

This project is to create a model that will take words in a subreddit post and predict which subreddit it belongs to. The main problem we're trying to solve is to help the company increase profit by using this model so we can help recommend related subreddits to users and keep them engaged and active on the site.

---
### Technologies:

- Programming Language
    - Python 3.7
    
- Imported Libraries
    - Pandas
    - Numpy
    - glob
    - Seaborn
    - Matplotlib.pyplot
    - Scikit-Learn: Did not use them all in the end, but did use them at one point for testing  
        - model_selection
        - linear_model
        - feature_extraction
        - pipeline
        - naive_bayes
        - tree
        - ensemble
        - metrics
    
--- 
### Data Description:

- Post_csv_files
    - Holds all the csv files of the posts pulled from the subreddits
    - Includes titles to the posts, the posts themselves, and the name of the relative subreddit

- Modeling.ipynb
    - Executive Summary 
    - Code
    
- Posts_Requests_Travel_vs_Shoestring.ipynb
    - Code for pulling the posts from the subreddits
    
- Subreddit_presentation.pdf
    - Presentation
    
- README.md

- travel_shoestring_df.csv
    - Dataframe with all posts from both subreddits combined
    - Kept separate from other datasets to prevent risk of change in data when cells in Modeling.ipynb are re-run
    
---
### Modeling Process Overview:

- Data cleaning
    - Imputed blanks into NaN fields
    - Dropped duplicates
    - Removed following using Regex minimizing risk of overfitting
        - Numbers
        - https 
        - Names of the subreddits
        - Term "subreddit" 

- TfidfVectorizer
    - max_features

- Modeling
    - Logistic Regression was the best
        - Regularized using Lasso improved model
    - Attempted GaussianNB and MultinomialNB. MultinomialNB worked better despite values being floats. Seems it treats the values the same as if CountVectorizer had been used
    - Attempted Random Forest Classifer using GridSearch

---
### Project Status:


Discovered the Logistic Regression was the best model and was improved when adding the Lasso regularization. Simplifying the model pevented overfitting, which can result from adding too many features. Other models were slightly overfit, but the cross val score and the score for the Test data were close, which indicates the sample data was not the issue. 

Next steps include adjusting the parameters for the Random Forest Classifier and using the Voting Classifer to find a model that has better performance.

---
### Contributing:


If you would like to contribute, please feel free to reach out to discuss any changes or suggestions you may have. 

---
### Source:

Data was pulled directly from Reddit for Travel and Shoestring subreddits.

Also referred to https://www.feedough.com/reddit-make-money-reddit-business-model/ for information about Reddit

