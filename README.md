(<img src="image/KICKSTARTER.jpg" width="600">)

# Machine Learning project on Kickstarter campaign success prediction

Our team would like to apply our machine learning skills to predict whether a Kick Starter project would be successfully funded based on the project category, launching month, duration, project location and the goal USD of the project. <br>

Data is from kaggle dataset: https://www.kaggle.com/yashkantharia/kickstarter-campaigns

## Table of Contents

- [Project background & aim](#Project_background_and_aim)
- [Data Collection](#Data_Collection)
- [Data Preprocessing](#Data_Preprocessing)
- [Model 1: Classification model](#Model_1:_Classification_model)
- [Model 2: Regression model](#Model_2:_Regression_model)
- [Conclusion](#Conclusion)
- [Challenge](#Challenge)
- [Room for Improvement & future application](#Room_for_Improvement_and_future_application)


## Project_background_and_aim

Starting a new venture and put your creative idea into real life can be exciting yet hard to complete as lack of capital. The global crownfunding platform KickStarter may create a great opportunity for you to make your dream come true. However, you may still hesitate as do not know if others also see your project as feasible and can get enough fund from the crownfunding. <br>

In this project, our team will act as a group of consultants in Kickstarter who would like to use Machine Learning models to predict whether the startup projects would be successfully funded. <br>

By developing a Campaign Success predictor to predict whether the project would successfully funded base on the project category, US/ Non-US country, release time and the goal USD of the project, would provide some direction for young entrepreneur and increase the success rate of start up projects. <br>

We would also like to further investigate if we would predict how much the project would be funded based on the project category, US/ Non-US country and release time to provide a guideline for our clients.<br>

## Data_Collection
Our dataset is from Kaggle, with 170K project entries (after cleaning duplicates) labeled as 'successful' or 'failed' as the crown funding 'status'. Also the amount of money funded is shown in USD dollars in 'USD pledge'. <br>

<img src="image/info.png" width="600">

In data preprocessing, duplicated data was dropped and there 

## Data_Preprocessing

### Imbalance of data
All projects labeled where the project based, classified into 15 categories and further to 159 sub-categories. However, there is a imbalance in data as majority of the projects are US-based and some sub-categories may not be very popular. The imbalance in data will easily affect our model prediction. <br>

#### Count plot for project based
<img src="image/country01.png" width="600">

#### Count plot for sub-category
<img src="image/subcategory.png" width="800">

Therefore, we decided to grouped all countries except US to Non-US based to have a better balance in data. For category, we only take main category to build the model. <br>

#### Count plot for project based - US or Non-US based
<img src="image/country02.png" width="600">

#### Count plot for main-category
<img src="image/maincategory.png" width="600">

### Bivariate analysis 

The crownfunding will consider as successful if the USD pledged online excess the goal of the funding. From the graph, it is obvious that the failed projects normally set an unrealistic high goal. <br> 

<img src="image/goal_USD.png" width="600">

The differerce in main category will also have different rate of success in crown funding. <br> 

<img src="image/maincategory_success.png" width="600">

Successful projects normally complete earlier than failed projects. <br> 

<img src="image/duration.png" width="600">

The final dataset for model develop. Categorical data will be one-hot encoded and numerical data will be normalized. <br> 
Model 1: Classification model <br> 
- predict whether the project can be successfully funded<br> 
- Dependent variable: status<br> 
- Independent variable: main_category, duration, goal_usd, country, start_month<br> 

Model 2: Regression model<br>  
- predict how much the project can be funded<br> 
- Dependent variable: usd_pledged<br> 
- Independent variable: main_category, duration, goal_usd, country, start_month<br> 

<img src="image/df.png" width="600">

## Model_1:_Classification_model
We developed three classification model, Logistic Regression, Random Forest Classifier and XGBoost Classifier with the below model performance. <br> 

In general, XGBoost Classifier better predict the sucessfulness of the project while Random Forest Classifier are slightly more sensitive to positive event as it has a higher recall. Since we would like to know the failure of project in a earlier stage. We chose the XGBoost model for the prediction.  <br>

<img src="image/classification_performance.png" width="600">

After fine tuning the XGBoost model, we developed the model at max-depth of 4 with accuracy of 0.69. <br>

<img src="image/XGBoost_performance.png" width="600">

## Model_2:_Regression_model

Since the successfulness of crown funding largely depend affected by whether the funding goal will match the public expectation. We would like to develop regression models to predict the amount of fund that can be raised. <br>

We tried Linear Regression model and Decision Tree Regression model. However, both models perform bad with low variance score of 0.017 and 0.028. It may because based on the current data, it is not sufficient to explain and predict the USD pleged from the crownfunding. <br>

### Linear Regression model performance 
<img src="image/linear_performance.png" width="600">

### Decision Tree Regression model performance 
<img src="image/tree_performance.png" width="600">

## Conclusion
As a conclusion, we chose the XGBoost model with parameter of max_depth = 4 for the prediction of the successfulness of the kickstarter projects. <br>

For the amount of USD pledged, since there is no suitable model for the prediction, more research and data will be needed to give a reliable suggestion on the goal amount for the project team to target on. <br>

## Challenge
1. Number of sub-category <br>
- The KickStarter classified the projects into 159 sub-categories. Due to hardware problem and imbalance of data, we are unable to use the feature for the model. <br>

2. Insufficient data for regression model<br>
- More features of the projects may required to find the relationship with the amount of USD that can be funded as the current dataset is not sufficient to develop a realiable regression model.<br>

## Room_for_Improvement_and_future_application
Since time is restricted in the project, we are unable to find a suitable model for the regression prediction. We would suggest to find out more features about the projects to understand how other people value a kickstarter projects.<br>

A more accurate classification model on the successfulness and a reliable regression model on the amount of fund prediction would helps young entrepreneurs know better about their projects and increase the rate of success. <br>
