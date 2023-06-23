# Baseball Classification
![Screen Shot 2023-06-22 at 2 49 51 PM](https://github.com/Kellyajara/Project3/assets/127794801/08954b05-588c-45db-8db1-e721f630687f)

By: Kelly Jara

## Overview
This project analyzes data on Major and Minor league pitchers, to classify whether or not a pitcher belongs in the Major or Minor league. After conducting EDA on the two data sets and combining them into one data frame, we were able to create a classification model to predict where a player should be in the leagues based on their pitching stats. 


## Business Problem
There are certain teams in the MLB that are unhappy with the way their pitchers are currently performing, especially those that were recently contracted onto the team. The MLB wants to explore the possibilities of signing/drafting more minor league players in hopes to bring in new pitchers with stats that match up with current major league players. 

## Data
Minor league data was obtained from fangraphs and Major league data was obtained from statcast. The data contains information from 2015-2023. Both datasets contained the following features: 
  - Name 
  - League - Whether the player is in the Major or Minor League
  - Pitches - Total amount of pitches thrown
  - G - Games Played (regardless of games started/completed)
  - W - Wins (as the pitcher, not team win)
  - L - Losses (as the pitcher, not team)
  - H - Hits
  - R - Runs
  - HR - Total number of home runs
  - SO - Strikeouts 
  - BB - Walks (intentional and unintentional)
  - ER - Earned Run
  - SV - Saves
  - BS - Blown Saves (when the pitcher had the opportunity to save the ball and failed) 
  - BK - Balk (When the pitcher makes an illegal throw or motion intended to deceive the baserunner or hitter)
  - ERA - Earned Run Average
  - WHIP - Walks & Hits per Inning Pitched
  - Oppo% - Opposite field percentage (balls that were pitched were hit but were thrown to the opposite field)
  - K% - Strike percentage
  - BB% - Walk percentage
  - WHIP Rank - Categorizing WHIP into ranks:
    * Poor
    * Below Average
    * Average
    * Above Average
    * Excellent
  - ERA Rank - Categorizing ERA into ranks:
    * Poor
    * Below Average
    * Average
    * Above Average
    * Excellent

Sources: 
  - https://www.fangraphs.com/
  - https://baseballsavant.mlb.com/statcast_search

## Modeling

After completing the EDA on the combined datasets, I began preprocessing and created a few models to see which one had the best metrics in classifying whether or not a player should be in the Major Leagues. 

### Base Model - Logistic Regression 

![LR Curve ](https://github.com/Kellyajara/Project3/assets/127794801/f64cb401-58f3-4700-ac1c-fa9b9ec14dcb)
![LR CM ](https://github.com/Kellyajara/Project3/assets/127794801/4bf08488-7cd1-4527-b600-73341ca98487)

  * In the Logistic Regression model, right off the bat, was performing fairly well. The model had a train and test score of 97.03% but and a precision score of 89.62%, which is still good but has room to do better.

### Decision Tree Model
![dt](https://github.com/Kellyajara/Project3/assets/127794801/baf302ee-820a-4c58-9970-b638a8365404)
  * The second model ran was a Decision Tree model. Decision Tree  models perform well when there are a lot of features in a dataset and are best used on datasets that have more complex and non-linear relations. This may not be this case in this dataset as rankings tend to be linear, but can become non-linear depending on the pitchers performance. (A pitcher can have great stats but because of other factors may not always receive a win as a pitcher, which can cause inconsistencies with certain stats).

![dt cm](https://github.com/Kellyajara/Project3/assets/127794801/9d1cc935-124f-4651-8817-fdcb0ae2e8b6)
![dt roc curve](https://github.com/Kellyajara/Project3/assets/127794801/c8284e1e-ea3b-4824-862c-15a0a440300c)


  * In the DT model, although the recall score improved, from being 90.90% to 92.82%, every other score dropped, which goes to show, that this is not the best model for this dataset.

### SMOTE - Logistic Regression Model 
  * Looking back through out the two models, I realized that there was an imbalance issue amoungst the target variable. There was a significant amount of minor league players compared to major league players, which may have caused overfitting in the previous models.

![imbalences](https://github.com/Kellyajara/Project3/assets/127794801/76f63269-2c0e-45dc-af9b-72f2610f161a)

  * Because there is an imbalance, the previous models were showing high accuracy scores due to the majority of the data lying in the minor leagues, and because of that, may not have taken into account the minor class, the Major leagues, which is something we need to consider in order to properly make our predictions.
  * By running a new logistic regression model, we are able to take care of the issue of having an imbalanced dataset and bring up our accuracy score to 97.68%, which is higher than our base model and dt model) as well as our other scores.

![smote roc](https://github.com/Kellyajara/Project3/assets/127794801/f7ac191c-da3f-4ed1-8ab6-88fed8b73b1d)
![smote cm](https://github.com/Kellyajara/Project3/assets/127794801/bb5e2af1-30b8-47eb-9edc-41c21c7f862e)

### Gridsearch KNN Model
  * KNN model goes through your data and based on your target creates classifiers that best represent that target. For example if a certain point belongs to one class, KNN model will then look at the "nearest neighbor" and classify those points to that class. Running through the KNN through gridsearch, it created a 5-fold cross validation, creates 5 splits within your data set and tests on each split.

![gs knn roc curve](https://github.com/Kellyajara/Project3/assets/127794801/91784340-cfba-4fe4-937e-50307fd43e62)
![gs knn cm](https://github.com/Kellyajara/Project3/assets/127794801/9f091216-cad7-4b3d-879b-7c9f0800551e)

  * In the KNN model, there was a small decrease in all the scores. The model had an accuracy score of 96.52%, which is lower than the previous models. 

### Random Forest - Best Model
  * In the Random Forest model, the train score was 99.90%, which indicated how well this model genralized the data used. Along with a high train score, the test score was also 97.90%, which shoes how well the model would perform in real-life scenarios. This model is able to accurately predit whether a minor league is ready to play for the major leagues 97.90% of the time.

![rf cm](https://github.com/Kellyajara/Project3/assets/127794801/4bde22e7-bb43-4d94-b7f7-38e1f72cb08f)
![rf dt roc curve](https://github.com/Kellyajara/Project3/assets/127794801/bac29f41-fb1a-447a-9352-174703f3cdfa)

## Feature Importance
  * Based on the best model, random forest, I then found which features were more important when classifying whether a pitcher should be in the major league. 
  - The top 5 being: 
    * Games played
    * Homeruns allowed
    * Blown saves
    * Saves
    * Innings Pitched

![feature importance](https://github.com/Kellyajara/Project3/assets/127794801/377ea40e-2841-4253-886d-83e9cfa024e7)

## Conclusion & Further Analysis
The classification model showed that there are 56 pitchers, who were originally classified as a minor league player, had stats that would classify them as major league players. To further prove the accuracy of the model, I looked up a few of the players listed and found that a handfull of them have, in the past year of 2023, signed onto major league teams. 

Being that the predictive model performed fairly well, there are few things that can be looked into to allow predictions to be more consice in terms of longevity of a players career and their consistancy as a pitcher. 
  * Things to look into: 
    * FIP (Field independent pitching)
    * Consistency - types of throws and how often the pitcher is able to land that specific pitch. 
    * Hitters - the types of hitters the pitcher is matched up against and how they perform.
    * Injuries - how prone to injuries that player is and if they have been off the roaster for 'x' amount of time. 
