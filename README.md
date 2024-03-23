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

* The target variable is right skewed, non-negative, continuous non zero variable (as appeared in the qq-plot).

<img width="448" alt="image" src="https://github.com/sallylee0801/Predicting-Building-Features-for-Energy-Cost-Reduction/assets/156154849/4fde7137-eb55-4eb8-821b-cd560114b7b1">

However, when comparing the GLM model with our baseline model, it appears that both models are poor fit for the data, warranting rejection of using the method.

### Machine learning Model (Random Forest)
Initially, we assessed the performance of different machine learning methods by calculating their RMSE (Root Mean Square Error) and r-squared values. RMSE quantifies the average difference between observed and predicted values by the model, while r-squared indicates the proportion of variance in the dependent variable explained by the independent variables. Our analysis revealed that the random forest model exhibited the lowest RMSE and the highest r-squared value among the methods evaluated.

<img width="397" alt="image" src="https://github.com/sallylee0801/Predicting-Building-Features-for-Energy-Cost-Reduction/assets/156154849/64e512c9-f793-4ff0-9f14-ecf5a4563c98">

Using Random forest, we conducted the feature importance. The significant features that impact the site_eui are:
- category_Warehouse_Service
- january_avg_temp
- build_age
- floor_area
- category_Living_Space

### Explainable AI (SHAP)
We use SHAP (SHapley Additive exPlanations) because it provides flexibility to understand feature importance both locally and globally, unlike Random Forest feature importance which does not explain individual instances. Additionally, SHAP enables us to demonstrate the direction of feature impact, making it a valuable tool for interpreting machine learning models.

<img width="405" alt="image" src="https://github.com/sallylee0801/Predicting-Building-Features-for-Energy-Cost-Reduction/assets/156154849/4464c0b7-0e50-4095-b59e-12c6dc8db72e">

Temperature: SHAP values indicate that temperature is a key factor influencing energy usage. Colder average temperatures in January tend to increase energy usage, likely due to higher heating demands.

Building Type: SHAP values show that the function of a building (e.g., warehouses or living spaces) strongly predicts energy usage. Different building types have varying energy needs, with some types requiring more energy than others.

Size: While size is a significant factor, SHAP values reveal that compact spaces may have higher energy use in certain instances. This could be due to less efficient use of energy or higher energy activities concentrated in smaller areas.


## Recommendation and Next Step
- Focus on Insulation and Heating Efficiency
Since January temperatures have a significant impact, improving insulation and heating efficiency in buildings could lead to substantial energy savings

- Differentiate by Building Type
Implement energy conservation measures tailored to different building categories, recognizing that warehouses, service areas, living spaces, and social institutions have unique energy profiles

- Analyze Small Space Energy Use
Investigate why smaller floor areas might correspond to higher energy usage. Consider energy audits to identify inefficiencies or high-energy-use equipment in smaller spaces

