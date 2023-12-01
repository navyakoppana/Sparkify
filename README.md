
# Sparkify- A Data Scientist Capstone Project

## Table of Contents

1. List of libraries used
2. Motive of the project
3. Files in the repository
4. Summary of the analysis
5. Acknowledgements

### List of libraries used

The following python libraries are imported for my analysis: Pandas,matplotlib,seaborn.

The following spark libraries are imported for my analysis:pyspark,SparkSession,sql.functions,sql.types,pyspark.ml -classification,evaluation,feature,tuning

### Motive of the project

Sparkify is an audio listening platform in which we try to estimate whether users are likely to stay based on their activity logs.

We have access to a JSON log of all actions performed by Sparkify users during a period of two months(October & November); our objective is to understand what behaviors can allow us to predict whether users will "churn" (i.e. unsubscribe from the service).

In order to achieve this, using 'Spark' framework we will extract the most relevant features from the log, train a machine learning classifier , fine tune it's parameters and with the help of accuracy and F1-score, determine the winning model.

### Files in the repository

a. Sparkify.ipynb-Jupyter notebook of sparkify project

b. Sparkify.html-HTML file of project

c. README.md- File giving the synopsis of the project

d. Sparkify_Blogpost.pdf-Blog post of the project explaining the project steps in detail.

e. mini_sparkify_event_data.zip-Compressed file of our mini dataset in .json format.

### Summary of the analysis

1. Loaded the json file using **'Spark'** framework and removed the rows with empty userId & sessionId arrives at the following conclusion: When we are dealing with the rows of empty userId , he/she is a ‘Guest’ and trying to ‘Register’ or ‘Submit Registration’. When we are dealing with the rows of empty sessionId , he/she has ‘Logged Out’ and trying to ‘Login’. As we removed both the rows, the following rows associated with those values are removed.

2. Create a column Churn to use as the label for the model using the Cancellation Confirmation events on the page column and explored the behaviour of users who stayed v/s who churned based on level(paid/free), gender(female/male),page, ts.

3. Plotted some visualisations of the behavior of users and arrived at following conclusions:

 a. The number of unique users are more active than cancelled users.
 
 b. Males are slightly predominant than females in both active and cancelled subscriptions.
 
 c. On the page list, the number of active users are way farther than cancelled users except for ‘Cancel’ and ‘Cancellation         Confirmation’ pages. Out of all pages, the highest number of active users are visiting ‘Thumbs Up’,’Home’,’Add to   playlist’,’Add to friend’ pages.
 
 d. Most of the users are listening to the songs between 15th and 18th hours.
 
 e. The no of users listening to the songs are increasing and decreasing , no particular trend is observed.
 
 f. As the data is limited to 2 months,There is not much data to explore about the number of users listening to songs in a particular month of the year.
 
4. Performed feature engineering and extracted the following features and combined them into a single dataframe for performing the next step modelling:-

 1) Total no of songs listened

 2) Gender

 3) Paid or Free users

 4) Average songs played per session

 5) Number of Thumbs up

 6) Number of Thumbs down

 7) Number of songs added to the playlist

 8) Total number of friends

 9) Churn(target)

5.Used vector Assembler and Standard Scaler to convert our numeric columns to vectors for ML modelling.Split the final dataset into train and test data in the ratio of 0.8:0.2.

6.Performance metrics:Accuracy,F1score and training time are chosen for reporting the results of all ML models.

7.The ML classification models which are used here are:

      a. Logistic Regression
 
      b. Random Forest Classifier
 
      c. Support Vector Classifier
 
8.The following conclusions are drawn from training and testing different ML models:

      a.Out of three ML models, Random Forest Classifier proves to be best model both in terms of F1score and accuracy.

      b.Cross validation and hyperparameter tuning doesn’t make much difference in output since the test dataset is a small      subset of data.

      c.With the tuning, parameters of Random Forest Classifier are best number of trees-10 and max depth of 10 best fit the   model.
 

### Acknowledgements

The links used for reference are acknowledged below:

https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.agg.html
https://stackoverflow.com/questions/36697304/how-to-extract-model-hyper-parameters-from-spark-ml-in-pyspark
https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.evaluation.MulticlassClassificationEvaluator.html
https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.evaluation.BinaryClassificationEvaluator.html
https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.classification.RandomForestClassifier.html#pyspark.ml.classification.RandomForestClassifier.numTrees
https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.classification.LinearSVC.html


```python

```
