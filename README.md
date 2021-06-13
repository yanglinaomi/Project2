# Project2
This contains all the stuff for Project2
## Problem Statement

Ames is a town in Iowa with a population of 66,258 in 2019. Ames is in Story County and is one of the best places to live in Iowa. Living in Ames offers residents an urban suburban mix feel and most residents rent their homes. In Ames there are a lot of bars, coffee shops, and parks. Many young professionals live in Ames and residents tend to lean conservative. The public schools in Ames are highly rated. At Ace Real Estate, we are passionate about helping our clients to find a dream house with affordable price. 

As the industry moves to automate the appraisal of house, Ace Real Estate decides to build up data science team to apply machine learning skill to estimate sale price of houses. As a member of the data science team, I will use Ames Housing data which collected from year 2006 to 2010 to build linear regression model to predict the sale price for houses in Ames and provide recommendation for homeowners to  increase their house value. 

## Executive Summary
The Ames housing dataset includes 80 features of nominal, discrete, ordinal and continuous variables for individual residential properties sold in Ames, IA from 2006 to 2010.

During the first step workflow which is data cleaning, missing values were detected and fixed, outlier points are investigated and eliminitated from the dataset. Once data cleaning is done, Exploratory Data Analysis (EDA) is conducted for each feature. Ordinal features are converted to discrete values. For categorical data (nominal), bar plots were created to visualize the mean Sale Price across categories. During EDA for categorical features, special attention was paid to any patterns or clusters in Sale Prices that emerged. I also expore continuous/discrete features with similar groups, like sold/built year, bathroom No and floor SF to create more meaningful new features. 

The linear relationship between Sale Price and all numeric features were examined using heatmap and correlation coefficients. Features with high correlation rate (>=0.4) were filtered out for visualization check. 
Features with continous data were plotted with scatter plot while features with discrete data were plotted with boxplot. 
Heatmap for all filtered-out features were also plotted to check colinear between features. If there was high colinearity between features, the feature with less correlation rate with Sale Price was removed from filtered features list. 

After filtered features list were comfirmed, train dataset was divided into training set (70% of data) and holdout set (30% of data) to prepare for modeling. In this project, 4 models (linear regression/ridge regression/lasso regression/elsticNET regression) were used. 

In the first verification, filtered features list with 27 features from EDA were used for these 4 models. Among these models, elasticNET had best MSE score. However, I observed that with higher Sale Price, the best fit of line did not fit well. In the high sale price side, the line tended to be curly. We decided to add square value (power 2) for some features which had high correction with saleprice to observe whether could improve MSE score and best fit of line in second verification. 

In the second verification, 6 square values (power 2) were added. The result showed much better MSE and slight improvement of best fit line for higher Sale Price. So I decided to try higher power into the features, i.e. add power 3 to verify whether higher power value could further improve the models in the third verification. 

In the third verification, 6 power 3 values were added. MSE scores were improved slightly. By checking lasso regression coeffient, some features' coeffients were zero. This may be due to high colinearity among the feature and its power 2 / power 3. In the fourth verification, features with zero coeffient were dropped. 


In the fourth verification, the MSE score almost had no improvement. However, we can observe the samll gap between train data MSE score and holdout data MSE score. R2 score for train dataset and holdout data set were 91% and 90% respectively. We can say that this model could fit train and holdout data well. 

After we identify our best model, residuals plot was evaluated and Sale Prices in test dataset were predicted. Interpretations and recommendations were made based off of the best-performing model.

## Table of Contents
1. Project Files
2. Data Dictionary
3. Model Selection
4. Conclusions and Recommendations

## Data Dictionary
A link to the data dictionary can be found [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)
)
## Model Selection
### 1 Model Verification - 1st round verification: Apply selected features
Model Verification - 1st round verification: Apply selected features
![image](https://user-images.githubusercontent.com/83536738/121801166-80881880-cc68-11eb-97c0-9bbdaaab9f54.png)



## Conclusion and Recommendations
The model created in project performances well for 90.57% of the variation in Sale Price of a property although it does not fit well for extreme high SalePrice. Power 2 features are added and this improves the prediction. However, higher power features (i.e. 3) does not help a lot to improve predictions but raises high vairance in linear regression and causes colinearity between features. After remove features with zero coeffients in lasso regression can make the model fit train dataset and holdout dataset better. Observed from histogram plots for SalePrice and some continous data features, they are not normally distributed and skew to one side. We may consider log-transfomration for further improvement of this model. 

From this model, we can make some recommendations for homeowners to increase their property value. 
  1. Maintain overall house quality including kitchen, internal and external of house etc.
  2. Increase floor area if possible 
  3. Make house well-renovated as good living quarters including basement area
  4. With builtIn or attached garage
  5. New houses and newly-renovated houses are more valuable. 
  6. The houses in neighborhoods, such as neighborhoods Stone Brook, Northridge Heights, Veenker, Northridge, Green Hills are more valuable. 

## Reference
[1] https://www.niche.com/places-to-live/ames-story-ia/
[2] https://en.wikipedia.org/wiki/Ames,_Iowa
[3] https://www.mortgageloan.com/are-automated-appraisals-the-wave-of-the-future#When-automated-makes-sense
