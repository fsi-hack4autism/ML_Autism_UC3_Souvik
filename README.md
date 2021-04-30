Predict Autism Diagnoses effectivenss using Various Machine Learning Models

Contributor: Souvik Mazumdar(Nasdaq)

![image](https://user-images.githubusercontent.com/8531740/116724901-d711fe00-a9fe-11eb-9f00-154c6591434b.png)

## Project Definition

This use case will analyze anonymized therapy data from a repository of Applied Behavior Analysis sessions and cases to draw insights which can be used by families, doctors and researchers to help understand the effectiveness of their programs

<hr/>

## Table of contents
* [Goals](#goals)
* [Project Analysis](#projectAnalysis)
* [Tools](#tools)
* [Setup](#setup)
* [Exploratoty Data Analysis](#eda)
* [Algorithm Analysis](#algorithmAnalysis)
* [Conclusion](#conclusion)
* [Future Scope](#futureScope)
* [References](#references)

## Goals

1)	Is 80% as a set goal indicative of future successes? 
a.	Are there data subsets that may use another target? 
b.	How would lagged / lead successes indicate future successes? 
c.	Would subsetting the target(s) in the data, such as by author, goal name, and/or goal domain, offer a better target variable(s)?  
2)	Using the goal set at 80%, or a variation found above, what are the descriptors of those who un/successfully complete goal outcomes? 
a.	Does age and / or sex effect un/succesful outcome? 
3)	What are the descriptors of the treatments for successful / unsuccessful goal outcomes?
a.	Does treatment intensity (defined as number of trials per day per week) impact outcome progress? ['sessionCount_byGoal_byDayYear'], ['sessionCount_byGoal_byWeekYear']
b.	Is there an optimum frequency / cadence of therapies? 
c.	What are the returns of intensity over time (i.e. steeper earlier and flatter later in the curve)?
4)	Are there variables around the therapist that predict better outcomes? 
a.	Do therapist changes in a goal affect outcomes? [‘trialStarts_byClient*’ *collectively use this byClient variable group]
b.	Does the number of therapists intervening towards a goal affect the outcomes? [‘authorChanges_byTrialId'], [‘authorChanges_byTrial_Outcome']
c.	Could the therapist effect positive outcomes by Goal? By Phase Mode? variables ['trialStarts_byAuthor_Outcome_Goal'], ['trialStarts_byAuthor_Outcome_Phase']
d.	Does the time it takes a therapist to chart sessions after data entry correlate with outcomes? [variable 'period_dataLogged_dataGraphed']
e.	Does the time in a session outside of charting data correlate with outcomes? ['period_graphedBySession']	
f.	Is there significance between outcomes and higher numbers of Goals? Higher numbers of Phase Modes? Different types of Phase Modes?

<hr/>

## Project Analysis

<hr/>

Standardized Data Preparation and Jupyter Notebooks

The data are processed in a standardized way using a Python script that prepares the data for the machine learning classifiers.

![image](https://user-images.githubusercontent.com/8531740/116727103-c2833500-aa01-11eb-982a-4c07591da381.png)

 Then we implement different models and accuracy validation techniques which as represented below.

![image](https://user-images.githubusercontent.com/8531740/116727663-7a184700-aa02-11eb-84ec-01c3821405c3.png)

<hr />

## Tools

<hr />

Jupyter Notebook: Write code in a virtual environment

Python libraries</bold>: numpy, pandas, seaborn, plotly, sklearn (dimensionality reduction, test-train split, gridsearch, cross-validation methods, evaluate performance)

Git: Track file changes

GitHub: Organize team workflow and project

Machine learning: Azure ML Studio

<hr />

## Setup

<hr />

1. clone the repo using git clone https://github.com/fsi-hack4autism/ML_Autism_UC3_Souvik.git
2. open the file autism_hack.ipynb in any python notebook and your ready to go

<hr />

## Exploratory Data Analysis

<hr />

Glimpse of the EDA done to understand the data

![image](https://user-images.githubusercontent.com/8531740/116728367-733e0400-aa03-11eb-8e8b-390361cdecf7.png)

This show the current goal status of the clients

![image](https://user-images.githubusercontent.com/8531740/116728670-d334aa80-aa03-11eb-8f46-ae1c1b3e452f.png)
 
Session Count Intensity Curve

![image](https://user-images.githubusercontent.com/8531740/116750761-92975a00-aa20-11eb-8393-fa55ecca3fb1.png)

We can analyse that with more sessions success rate is high. So more sessions should be organised per day/month/year. Highest Concentration of successes is in the initials sessions. So if regular sessions are kept in the initial days, the success rate will be higher. 
 
![image](https://user-images.githubusercontent.com/8531740/116728788-f95a4a80-aa03-11eb-8f49-be86a6657cf2.png)

Correlation Matrix for all dependent variables

<hr />

## Algorithms Analysis 

<hr />

![image](https://user-images.githubusercontent.com/8531740/116728922-27d82580-aa04-11eb-80d4-a9320cc567b6.png)

Line Plot to show Test Score vs Train Score

Confusion Matrix

![image](https://user-images.githubusercontent.com/8531740/116729050-5229e300-aa04-11eb-82cb-abf07bb788da.png)

| F1 Score      | Precision Score         | Recall Score  |
| ------------- |:-------------:| -----:|
| 0.9918818722131946     | 0.9931865209378359 |0.9906003851387001 |

Accuracy Matrix using Random Forest Algorithm

What do these scores mean?

We get the highest accuracy for Random Forest, with the score reaching 99%. This implies, our model predicted classified correctly 99% of the times. 
The Precision score stood at 0.99, implying our model correctly classified observations with high importance 99% of the times. 
The Recall stood at 0.99. We also have an F1 score of 0.99. 
The F1 score is the harmonic mean of precision and recall. It assigns equal weight to both the metrics.
However, for our analysis it is relatively more important for the model to have low false negative cases(Where the client is improving with the sessions).

![image](https://user-images.githubusercontent.com/8531740/116730563-450df380-aa06-11eb-8167-d2f4fcb86524.png)

Among our dependents which features are have the most importance

<hr />

## Conclusion

<hr />

We thus select the Random Forest Classifier as the right model due to high accuracy, precision and recall score. 
One reason why Random Forest Classifier showed an improved performance was because of the presence of outliers. 
Random Forest is not a a distance based algorithm hence it is not much affected by outliers. 
Whereas distance based algorithm such as Logistic Regression and Support Vector showed a lower performance. 
Based on the feature importance, Author Changes is the most important factor which can determine a success trial. 
Other factors also contributes to the prediction. As we can see, the results derived from Feature Importance makes sense as one of the first things that actually affects the outcomes.

<hr />

## Future Scope

<hr />

Analyzing the Goals by clustering them and assigning the most suited goal for each individual.

More variables to be considered for evaluation success.

<hr />

## References

<hr />

Creating ReadMe files : https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project

Implementing Algortihms: https://www.analyseup.com/learn-python-for-data-science/python-random-forest-feature-importance-plot.html#:~:text=Tree%20based%20machine%20learning%20algorithms,trying%20to%20predict%20the%20target.

Autism Study : https://www.kaggle.com/faizunnabi/autism-screening-classification

Special Thanks to all the Event Organizers of the Hackathon https://fsi-hack4autism.github.io/#about
