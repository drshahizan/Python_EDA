
# Assignment 4: Feature Engineering

**GROUP NAME: KICAP SAMBAL**

**TEAM MEMBERS:**
```
MOHD NOR BIN MOHIDIN (MCS231008)
NABILA HUSNA BINTI ROSLI (MCS231009)
NUR AZIMAH BINTI MOHD SALLEH (MCS231011)
ZUHAYR ARIF BIN ZAKARIA (MCS231002)
```

## Introduction

### **FLIGHT PRICE PREDICTION**

#### **Dataset**
The dataset contains information about flight booking options from the website Easemytrip for flight travel between India's top 6 metro cities. There are 300261 datapoints and 11 features in the cleaned dataset.

#### **Features**
The various features of the cleaned dataset are explained below:
1. `Airline`: The name of the airline company is stored in the airline column. It is a categorical feature having 6 different airlines.
2. `Flight`: Flight stores information regarding the plane's flight code. It is a categorical feature.
3. `Source City`: City from which the flight takes off. It is a categorical feature having 6 unique cities.
4. `Departure Time`: This is a derived categorical feature obtained created by grouping time periods into bins. It stores information about the departure time and has 6 unique time labels.
5. `Stops`: A categorical feature with 3 distinct values that stores the number of stops between the source and destination cities.
6. `Arrival Time`: This is a derived categorical feature created by grouping time intervals into bins. It has six distinct time labels and keeps information about the arrival time.
7. `Destination City`: City where the flight will land. It is a categorical feature having 6 unique cities.
8. `Class`: A categorical feature that contains information on seat class; it has two distinct values: Business and Economy.
9. `Duration`: A continuous feature that displays the overall amount of time it takes to travel between cities in hours.
10. `Days Left`: This is a derived characteristic that is calculated by subtracting the trip date by the booking date.
11. `Price`: Target variable stores information on the ticket price.

The code for feature engineering involves importing necessary libraries, loading the dataset, performing preprocessing steps, and conducting exploratory data analysis (EDA). Key features are extracted, new columns are created, and visualizations are generated to understand the dataset.

## Task Overview
The feature engineering task includes preprocessing the flight dataset, creating new features, and selecting relevant features for a machine learning model. Exploratory data analysis is performed to gain insights into the dataset. The code covers steps such as handling categorical variables, creating derived features, and preparing the data for predictive modeling.

A new preprocessed DataFrame (`df_preprocessed`) is created. Columns are extracted or transformed from the original `flight_df` DataFrame. Notable preprocessing steps include formatting departure and arrival times, converting stops information, extracting flight duration in hours, and handling the price column.

Two new columns are added to the original flight_df DataFrame, namely '`departure_hour`' and '`departure_minute`'. These columns are obtained by extracting the hour and minute components from the 'dep_time' column, representing the departure time.

Two additional features are created: '`is_early_morning`' and '`is_late_night`'. These binary features indicate whether a flight departs in the early morning (between 4 AM and 8 AM) or late at night (after 10 PM or before 4 AM), respectively.

Perform **feature selection** for a machine learning model. It selects a subset of features from the original dataset to be used as `input variables (X)` for predicting the `target variable (y)`.

* X: This is the feature matrix, representing the input variables for the machine learning model. It is created by selecting specific columns from the flight_df DataFrame. The selected columns are:

 * '`departure_hour`': The hour of the departure time.
 * '`departure_minute`': The minute of the departure time.
 * '`stop`': The number of stops (categorical variable).
 * '`is_early_morning`': A boolean indicating whether the flight is in the early morning.
 * '`is_late_night`': A boolean indicating whether the flight is in the late night.

* y: This is the target variable, representing the variable we want to predict. In this case, it is the flight price, and it is extracted from the 'price' column of the flight_df DataFrame.

* **X**: The feature matrix containing the selected features for training and testing.

**y**: The target variable (in this case, the flight prices).

**test_size**: This parameter determines the proportion of the dataset to include in the test split. In this case, it's set to 0.2, meaning that 20% of the data will be used for testing.

**random_state**: This parameter ensures reproducibility by fixing the random seed. The same random seed will yield the same train/test split every time the code is run.

The function returns four variables:

* `X_train`: The training data (features) obtained by splitting X.
* `X_test`: The testing data (features) obtained by splitting X.
* `y_train`: The training data (target variable) obtained by splitting y.
* `y_test`: The testing data (target variable) obtained by splitting y.


## Conclusion
The feature engineering process enhances the dataset for flight price prediction. New features like 'is_early_morning' and 'is_late_night' provide insights into the temporal aspects of flight departure times. Categorical encoding and feature scaling contribute to preparing the data for machine learning. The code sets the stage for building predictive models by selecting important features and demonstrating initial data exploration.

* **Feature Importance:**
The code includes a Random Forest model, and the feature importance plot helps identify which features have the most significant impact on predicting flight prices. This information can be crucial for understanding the factors that influence pricing.

* **Feature Engineering:**
The code demonstrates feature engineering techniques, such as extracting information from the 'departure_time' column and creating new features like 'is_early_morning' and 'is_late_night.' This suggests that specific times of the day may be important predictors for flight prices.

* **Hyperparameter Tuning:**
The code includes a grid search for hyperparameter tuning, indicating an effort to optimize the Random Forest model for better performance. The best hyperparameters found from the grid search can guide future model training.

* **Data Preprocessing:**
The code showcases data preprocessing steps, including handling categorical variables ('stop') through label encoding, scaling numerical features, and dealing with missing values. These steps contribute to a cleaner and more robust dataset for modeling.

* **Visualization:**
Visualizations, such as the boxplot of price by airline, provide insights into the distribution of prices among different airlines. This could help in understanding the pricing strategies of different airlines.

* **Mean Squared Error (MSE):**
The code calculates the Mean Squared Error (MSE) as a metric for evaluating the model's performance on the test set. A lower MSE indicates better predictive performance. You can analyze the MSE to assess how well the model is capturing the variance in the flight prices.

