# Optimal-Model-Selection

Aim to test varied machine learning models and find the optimal model to use to analyze our dataset.

Data cleaning and initial steps:

Problems we had:
- Categorical Variables
- Standardizing the dataset
- Omitting empty pieces of data

Solutions:
- One-hot encoding values: 
  - Used for analyzing categorical variables by turning them into binary numbers
  - Able to use PCA for the analysis
- Used StandardScalar package to scale/standardize dataset for PCA
  - Dropped null values
 
Building our model:

ML methodologies that we initially looked into and ran preliminary tests on:
Linear Regression (OLS)
Ridge Regression
Lasso Regression
Neural Networks
Auto Regressive
Principal Component Regression (PCR)
Random Forest

<img width="347" alt="Screenshot 2025-01-03 at 1 21 21 PM" src="https://github.com/user-attachments/assets/a6028b4b-31fa-4276-b171-81003672acf8" />

The models we ended up conducting tests on were Linear Regression (OLS), Ridge Regression, Lasso Regression, Neural Networks, Principal Component Regression (PCR), and Random Forest. We didn’t follow through with the Autoregressive model because that requires time series data, and that isn’t what we’re dealing with here. The OLS Model was the base model we used to compare the others with to ensure higher accuracy and better model fit. We were also able to compute a list of top 26 most important features using PCA with models excluding neural network, which we used a separate technique for discussed in the later slides.

Initial Idea: Utilizing Principal Components Analysis (PCA) for Ridge and LASSO Models

Why PCA to Analyze?
In order to test certain regression models, dimensionality reductions need to be made in order to reduce complexity of the multitude of variables
We were able to reduce the dimensionality to contain only the important pieces of information

PCA Analysis:
Calculate explained variance to determine which feature contributes the most information to principal components (higher percentage = more significant contribution towards capturing variability in data across multiple principal components)

Results Pt.1 (Model selection):

Based on preliminary testing:
Random Forest regression is the best model for the job because it produced the highest R^2 (0.51) and lowest MSE values (519126.85)
This means that the random forest model indicates a better fit with the predicted data than the other models
Robust in handling datasets that are not rigidly linear while preventing overfitting
Able to handle categorical data for dataset (i.e “State”, “Region” etc.) without extensive pre-processing
Utilizing multiple trees (“ensemble approach”) reduces impact of certain outliers and noise in the fast-food franchise dataset 

OLS Model:

<img width="370" alt="Screenshot 2025-01-03 at 1 22 59 PM" src="https://github.com/user-attachments/assets/059255e9-545d-4a7d-bc25-343007793f1d" />

Results Pt. 2 (Feature Importance):

We computed feature importance with random forest in order to determine the most influential features towards restaurant sales. We found that some of the most important variables include income class/income, state, area, number of seats, competition.
Feature importance in our Random Forest regression model quantifies the impact of each variable on predicting burger sales. Calculated across multiple decision trees, we aggregate how effectively a feature enhances prediction accuracy. The resulting scores offer insights into the crucial factors influencing our model's ability to forecast sales for the Flying Cow chain.

<img width="299" alt="Screenshot 2025-01-03 at 1 24 05 PM" src="https://github.com/user-attachments/assets/823370db-4eaf-4d50-a190-60583e8a6073" />

Results pt.3 (Final recommendations):

We believe that Flying Cow Burgers should utilize the Random Forest Method to predict quantities sold in the future because it has the best fit with the current quantity pattern seen throughout the different variables given.
We stress that the main variables to be looked at are overall income of customers and number of seats/size of restaurant.

The model suggests that income levels, particularly the upper income class, are the most predictive of burger sales. This implies that stores located in wealthier areas have higher sales, potentially due to higher disposable income. We recommended to prioritize expansion in affluent areas and consider product lines that cater to this demographic, and therefore raise company sales. We also noticed that the size of the restaurant and the number of seats are important, indicating that larger restaurants might perform better. We recommend that when opening new restaurants or renovating, consider designs that maximize seating capacity without sacrificing customer comfort. The middle and low-middle income classes also appear to be significant variables to burger sales. We recommend to tailor the menu and pricing strategies to be attractive and accessible to these income classes.


https://scikit-learn.org/stable/auto_examples/ensemble/plot_forest_importances.html
https://medium.com/mlearning-ai/predicting-store-sales-random-forest-regression-b77abec64c17
https://towardsdatascience.com/5-machine-learning-techniques-for-sales-forecasting-598e4984b109

