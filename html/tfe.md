# Taxi Fare Estimator
A regression model to estimate taxi fares before the ride, based on data collected by the NYC Taxi and Limousine Commission (TLC).

## Overview 
The goal of this project was to develop a regression model to estimate taxi fares prior to the ride. The predicted fares will serve as an input for a subsequent machine learning project. This project utilized yellow taxi trip data from New York City collected in 2017.

After analyzing the characteristics of 18 features and their relationships with the target variable (fare amount), six of the most influential features were selected or engineered. A **multiple linear regression model** was then developed, achieving an **R² score of 0.88** when evaluated on the full dataset — meaning that approximately **88% of the variance** in fare amounts is explained by the model, demonstrating strong predictive performance.

## Data Understanding
The dataset, sourced from NYC.gov, contained approximately 408k unique trips with 18 features, including trip duration, pickup and drop-off locationIDs, vendor information, toll amounts, and payment type, etc. 

Both the fare_amount and trip_distance (as well as duration) contained unreasonable values and outliers. To ensure the integrity of the regression model, these data points were capped at reasonable maximum and minimum values to avoid any distortion. The outliers were highlighted in the below plot with larger spots and yellow color.

Since the actual trip distance and duration are unknown before the ride begins, historical trip records were leveraged to compute the average distance and average duration between pickup and drop-off points.

<img alt="Impact of Distance on Fare Amounts" src=/images/x-Trip_distancey-Fare_amount.png>

These averages showed a strong correlation with fare amounts, as illustrated in the heatmap below.

<img alt="Correlation Heatmap" src=/images/heatmap.png>

## Modeling and Evaluation 
Because the input variables (X) had very different scales, all features were standardized to improve model performance.

Trips to and from JFK Airport were excluded from model training because airport trips use fixed fares. During prediction, such trips were directly assigned the fixed fare of $52.

There was also a potential data leakage issue involving the mean_duration and mean_distance features: when averages were computed from the entire dataset, information from the test set could inadvertently influence the model. To mitigate this, during testing, averages were recalculated using only the training data wherever possible.

The model performed well on both the training and test datasets, suggesting minimal bias and no significant overfitting. On the training set, the model achieved an **R² score of 0.839**. On the test set, the model achieved an **R² score of 0.779**.

<img alt="Model Result on full data" src=/images/model_result_on_full_data.png>

## Conclusion
Since the regression model was trained with standardized features, the interpretation is that for every 2.81mile increase in distance, the predicted fare increases by approximately $6.05. Reframed in a more intuitive way, for each additional mile, the fare is expected to increase by about $2.35 (calculated as 6.05 ÷ 2.81).

---
[My name is Yvette](https://yvette-yl.github.io/ "Welcome to My Profile")  |  [Proposel](/PACE_Strategy.md "")  |  [Python Notebook](/.ipynb "")  |  Presentation  | 
