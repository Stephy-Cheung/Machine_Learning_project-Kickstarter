(<img src="KICKSTARTER.jpg" width="600">)

# Machine Learning project on Kickstarter campaign success prediction

Our team would like to apply our machine learning skills to predict whether a Kick Starter project would be successfully funded based on the project category, launching month, duration, project location and the goal USD of the project. <br>

Data is from kaggle dataset: https://www.kaggle.com/yashkantharia/kickstarter-campaigns

## Table of Contents

- [Project background & aim](#Project_background_and_aim)
- [Data Collection](#Data_Collection)
- [Data Preprocessing](#Data_Preprocessing)
- [Assumption](#Assumption)
- [Analysis](#Analysis)
- [Conclusion](#Conclusion)
- [Challenge](#Challenge)
- [Room for Improvement & future application](#Room_for_Improvement_and_future_application)


## Project_background_and_aim

Starting a new venture and put your creative idea into real life can be exciting yet hard to complete as lack of capital. The global crownfunding platform KickStarter may create a great opportunity for you to make your dream come true. However, you may still hesitate if others also see your project as feasible and can get enough fund from the crownfunding. <br>

In this project, our team will act as a group of consultants in Kickstarter who would like to use Machine Learning models to predict whether the startup projects would be successfully funded. <br>

### Business Problem

The major problem we would like to solve is to develop a Campaign Success predictor to predict whether the project would successfully funded base on the project category, US/ Non-US country, release time and the goal USD of the project.  <br>

We would also like to further investigate if we would predict how much the project would be funded based on the project category, US/ Non-US country and release time to provide a guideline for our clients.<br>



## Data_Collection
Our dataset is from Kaggle, with 170K project entries (after cleaning duplicates) labeled as 'successful' or 'failed' as the crown funding 'status'. Also the amount of money funded is shown in USD dollars in 'USD pledge'. <br>

<img src="info.png" width="600">

-------------(Below part is waiting for update)---------------------------------------------
## Data_Preprocessing
In data preprocessing, duplicated data was dropped according to unqiue res_id provide by Openrice.com and we have screened out restaurant that with number of reviews less than 5. <br>
<img src="image/code_preprocess.png" width="600">

The district is extracted from the English full address. However, there are restaurants that only provide Chinese address which cannot be processed. We look into each Chinese address and classified the distric manually. <br>
<img src="image/code_address_in_Chi.png" width="600">
<img src="image/code_address_in_Chi2.png" width="600">

We also discovered that the cuisine column returns location instead of cuisine name since they provide fusion cuisine. The invalid entries are changed to 'fusion' manually.<br>
<img src="image/code_preprocess_cuisine2.png" width="600">

## Assumption
Since the financial performance of individual restaurant is not available, we have assumed that the more popular the restuarnt is, the higher the profitability. <br>

In our target data, Number of 'likes', 'dislikes', 'bookmarks' and 'review' reflected the popularity of the restaurant. Since we found there is high correlation between 'bookmarks' and 'review'. We create the popularity index as below for analysis.  

Popularity Index = Number of bookmarks x Like precentage<br>

<img src="image/Correlation_table.png" width="600">

## Analysis
### 1. Location
Causeway Bay, Central, Sheung Wan, Wan Chai, Repulse Bay are the top 5 location for Japanese restaurant popularity index. 
<img src="image/Analysis_location.png" width="600">

### 2. Price range
High menu pricing of above HK$800 per pax has the highest popularity.
<img src="image/Analysis_price.png" width="600">

### 3. Cuisine
The all-you-can-eat restaurant has the highest popularity in cuisine.
<img src="image/Analysis_cuisine.png" width="600">

## Conclusion
As a conclusion, we would recommend our client to open the new restaurant as an all-you-can-eat Japanese restaurant with a price-range of HK$800 or above. In location, we would like to provide the top 5 location of Causeway Bay, Central, Sheung Wan, Wan Chai and Repulse Bay as consideration as there are large number of Japanese restaurant in location like Causeway Bay and Central and the market may be saturated.

## Challenge
1. Number of returns on each search - We discover that Openrice.com only return 250 entries for each search and therefore, we have separate the web-scrapping process in batches, followed by drop duplicates to obtain the full dataset.

2. Invalid entries - Invalid entries in 'District' and 'cuisine' found and amended manually during data processing mentioned in the above section.

## Room_for_Improvement_and_future_application
To further enhance the project, a more sophisticated model is required to better evaluate the profitability and popularity of the restaurants. Consider additional data source such as websites like TripAdvisor, revenue of individual restaurant and timeframe of the reviews would further improve the validity of our analysis.  <br>

The above analysis can be applied on various cuisine and locations in Hong Kong to assist different restaurant opening.
