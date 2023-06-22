# Baseball Classification
![Screen Shot 2023-06-22 at 2 49 51 PM](https://github.com/Kellyajara/Project3/assets/127794801/08954b05-588c-45db-8db1-e721f630687f)

By: Kelly Jara

## Overview
This project analyzes data on Major and Minor league pitchers, to classify whether or not a pitcher belongs in the Major or Minor league. After conducting EDA on the two data sets and combining the two into one data frame, we were able to create a classification model. The best model being Random Forest. 


## Business Problem
There are certain teams in the MLB that are unhappy with the way their pitchers are currently performing, especially those that were recently contracted onto the team. Working together with the MLB, we want to explore the possibilities of signing more minor league players in hopes to bring in pitcers with stats that match up with current major league players. 

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

## Modeling

After the EDA was completed on both data sets and were combined,  

## Results

## Conclusion

## Further Analysis
Being that the predictive model performed fairly well, there are few things that can be looked into to allow predictions to be more consice in terms of longevity of a players career and their consistancy as a pitcher. 
