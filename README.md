C# Project 2 - Ames Housing Data and Kaggle Challenge
Tenzin Wangdu | 3.07.2021

### Problem Statement
---
* A Realtor is looking to renovate and build houses in Ames, Iowa. 
* Look the data to see what to invest in to get best R.O.I. 
* Which features will raise the price of the house value.
    

### Table of Contents
---
- [Data Collection](#Data_Collection)
- [Data Dictionary](#Data_Dictionary)
- [Data Import & Cleaning](#Data_Import_&_Cleaning)
- [Exploratory Data Analysis](#Exploratory_Data_Analysis)
- [Data Visualization](#Data_Visualization)
- [Modeling](#Modeling)
- [Conclusions and Recommendations](#Conclusion_and_Recommendations)
- [Soruces](#Sources)

### Data_Collection
---
Data is from the Kaggle ('https://www.kaggle.com/c/dsir-28-project-2-regression-challenge/data'). Train data contains all of the training data for your model. Test data contains the testing data for your model. Also, there is a sample_sub_reg.csv where the prediction data is compared to this data for Sale Price.

### Data_Import_&_Cleaning
---
After importing the data using pandas, checking for null values and error. By looking at the data dictionary, I dealt with different missing features for every columns. Mainly for discrete, I use fillna method with the mode and continuous with mean by using fillna. There are many missing values for ordinal value that were misconstrue by NA with missing values.

### Data_Dictionary
---
The link contains all the data dictionary for the dataset
http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

### Exploratory_Data_Analysis
---
The summary statistics of the data is Sale Price is between 20,000 to 600,000. The best correlation between the saleprice and features were overall quality of the house. 
Features that have the best correlation to the Sale Price
1. Overall Qual
2. Gr Liv Area
3. Garage Area  
4. Garage Cars
5. Total Bsmt SF
6. 1st Flr SF
7. Year Built
8. Year Remod/Add
9. Full Bath 
10. TotRms AbvGrd 
11. Mas Vnr Area
12. Fireplaces
However, that doesn't tell the whole story as we need to look at coef_ of the model to determine which affects the sale price the most. 
- Overall Quality, condition, age and location of the house are the most essential in increasing the sale price.
- In Order to Get the best ROI
1. Invest in Stone Brook, Northridge Heights and Northridge
2. Add a fireplace(if not already)
3. Renovate the garage if it is in bad condition
4. Having more room above ground
5. Newer Houses
6. Having 2 or more Story substantially increase the price

### Data_Visualization
---
This shows the Sale Price Distribution

<img
     src = "https://git.generalassemb.ly/tw1270/Submissions/blob/master/projects/project_2/Images/price_distribution.png" style = '' style="float: left; margin: 20px; height: 55px">

This shows the Top 10 Location of the house price

<img
     src = "https://git.generalassemb.ly/tw1270/Submissions/blob/master/projects/project_2/Images/location.png" style = '' style="float: left; margin: 20px; height: 55px">

Feature Correlation to Sale Price

<img
     src = "https://git.generalassemb.ly/tw1270/Submissions/blob/master/projects/project_2/Images/price_correlation.png" style = '' style="float: left; margin: 20px; height: 55px">
     
Top Feature with above 50% correlation

<img
     src = "https://git.generalassemb.ly/tw1270/Submissions/blob/master/projects/project_2/Images/topfeature.png" style = '' style="float: left; margin: 20px; height: 55px">

### Modeling
---
Started off feature engeering the all the object columns in both train and test data and then combine them into one and then using iloc to separate them later. 
#### Linear Regression:
Testing Score: 0.9127113956404701, Training Score: 0.9459142319129037
Testing RMSE-22842.094019513348, Training RMSE: 18614.36565098399

The model is overfitted as the training score and training RMSE are performing way better than the testing score. 
#### Ridge Model:
Training Score: 0.9168119115686862, Testing Score: 0.9065915922723498
Testing RMSE: 23629.260187166485 Training RMSE: 23085.39512836994

The Ridge model perform worse in the rmse than the linear Regression. However, it has variance and bias trade-off. It is similar in value in both test and train score and rmse
#### LASSO Model
Training Score: 0.9345870665164082, Testing Score: 0.9210134933815587
Testing RMSE: 21728.692462391853 Training RMSE: 20470.97617279104

Lasso Perform the best out of the Linear Regression and ridge, as it gives score of 92 on test and 21728 on the rmse.

#### Baseline Model
Testing RMSE: 77354.3252026887, Training RMSE: 80039.93732744697
All of the model beats the baseline model by a lot. Lasso performs the best with testing score of 93% and RMSE of 21728. Which beats the baseline by more than 50,000. 

### Conclusion_and_Recommendations
---
Overall Quality, condition, age and location of the house are the most essential in determining the sale priceIn Order to Get the best ROI, invest in Stone Brook, Northridge Heights and Northridge
- Add a fireplace(if not already)
- Renovate the garage if it is in bad condition
- Having more room above ground 
- Newer Houses
- Having 2 or more Story substantially increase the price

### Sources:
---
* Data Sets: https://www.kaggle.com/c/dsir-28-project-2-regression-challenge/data
* Data Dictionary: http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

