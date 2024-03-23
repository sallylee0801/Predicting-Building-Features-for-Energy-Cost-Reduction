# Predicting-Building-Features-for-Energy-Cost-Reduction

## Team Member
- [Sally Lee](https://github.com/sallylee0801)
- [Kevin Ko](https://github.com/kevinkooo)
- Lin Sabones
- Vanessa Leal

## Project Overview
### Objective
This project aims to identify building features correlated with high energy consumption to help buyers and investors reduce energy expenses effectively using a dataset comprising building characteristics, geographical data, and local weather patterns.
### Data Profile
- U.S. coverage over 7 years 
- 62 features, +75k observations
- Captures energy usage across various building types
- Each row corresponds to a specific building facility at a distinct location
- Target: site_eui (Site Energy Usage Intensity)

## Approach
### Feature engineering
To be able to conduct precise feature selection, we started with feature engineering to eluminate nuances in the data
<img width="915" alt="image" src="https://github.com/sallylee0801/Predicting-Building-Features-for-Energy-Cost-Reduction/assets/156154849/e77a11fe-c09b-4e1c-9b4c-b0118d879f7a">

### Linear Regression Model (GLM)
The first model engineering method we use is GLM model, as the target variable appears to be a Gamma distribution, we will be comparing it with our baseline model (OLS)

<img width="431" alt="image" src="https://github.com/sallylee0801/Predicting-Building-Features-for-Energy-Cost-Reduction/assets/156154849/01fde7f0-434a-49b3-af8a-d1f50654bc80">

* The target variable is right skewed, Non-negative, Continuous non zero variable (as appeared in the qq-plot).

<img width="448" alt="image" src="https://github.com/sallylee0801/Predicting-Building-Features-for-Energy-Cost-Reduction/assets/156154849/4fde7137-eb55-4eb8-821b-cd560114b7b1">

However, when comparing the GLM model with our baseline model, it is appears that both models are poor fit for the data, warranting rejection of using the method.

### Machine learning Model (Random Forest)
We started by calculating the RMSE and r-squared of each machine learning method, RMSE measures the average difference between the observed values and the predicted values by the model
where as R-squared value represents the proportion of variance in the dependent variable that is explained by the independent variables in the model. We found that =random forest= has the lowest RMSE and highest r-squared

<img width="397" alt="image" src="https://github.com/sallylee0801/Predicting-Building-Features-for-Energy-Cost-Reduction/assets/156154849/64e512c9-f793-4ff0-9f14-ecf5a4563c98">



