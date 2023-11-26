## Exploratory Data Analysis of Brooklyn Home Sales, 2003 to 2017
### Team Composition
| Name                             | Matric Number |
|----------------------------------|---------------|
| Pang Chern Hong             |MCS231006      |
| Wu JiaMing             |MCS221033      |
| Liu KaiYuan            |MCS231020      |
| Nian Cong             |MCS231007      |

### Introduction
The project dives into Broollyn home sale dataset to understand the factors that affect the house prices and discuss the method to analyze and estimate the sale price of the brooklyn's houses. The goal was to find the features that affect the most on the sale price of brooklyn houses and make an estimation, giving the information such as zipcode, distance to school, lot area, address and others. The analysis aims to answer questions about mutual informations of the features to the house prices, and how is the performance of regression on the estimation of sale prices.

Since we used the same dataset for assignment 3 and assignment 4, the latter regression model and explanation will be presented at the assignment 4.

### Big Data Tools Selection
Sklearn, paired with Python's Pandas, Matplotlib, and Seaborn, are the main tools for managing and visualizing the large volume of data.

### Data Loading
Essential libraries are installed, and data is downloaded from kaggle and being read from google drive.

### Data Cleaning and Preprocessing
We find the invalid values, duplicate data, and outliers to prepare the data for a better analysis and prediction.

### Exploratory Data Analysis
#### Statistical Summary
A statistical overview of the land aread in sqft, year of built, distance from school, lot area, year of sale is presented.

#### Uncover Patterns and Anomalies
The team discusses correlations found within the dataset, like the PCA components relationship and the mutual informations between the features and the sale_price.

### Conclusion
The dataset suggests that despites the lot area and the land area of the houses, the address of the houses is the primary factors that affect the house prices, the performance of the regression model is not that accurate but still possess certain reference value and basically can provide us the insights to get the prediction of the sale price.

