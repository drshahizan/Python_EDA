# Assignment 3: Exploratory Data Analysis (EDA) Using Big Data

### Group Name: RAM
### Group Members:

| Name          | Matric Number  | 
| ------------- | -------------- | 
|MOHAMMED RAZA ASFAK CHIDIMAR     | MCS231004       | 
| AYAZ RAHMAN BHUIYAN    | MCS231023       |
|MUSAB IBNE AHMAD  | MCS231017        | 
| HUSSEIN YUSUF SHEIKH MOHAMED   | MCS231024       |

### 📂 Google Colab file:
<a href="https://colab.research.google.com/drive/1K3dfFbObDE34pItBnr86Lp4N3EhvqY7R?usp=sharing" target="_parent">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>


## Introduction:
The dataset presented is focused on the prediction of water quality and consists of 5,956,842 entries with 24 columns. The dataset contains many indicators, including pH, iron concentration, nitrate concentration, chloride concentration, and others. Also, there are environmental elements such as water and air temperature, month, day, time of day, and an outcome variable. The objective of this analysis is to explore the dataset, discover patterns, trends, and outliers, and gain knowledge about the distributions and correlations among variables.


## Task Overview

### Data Selection and Preprocessing

* Used the Kaggle API and Google Colab for importing the dataset.
* Analysed the dataset, identified and displayed the 24 columns and 5,956,842 entries.
* Checked for missing values, removed columns that were not necessary (Index, Air Temperature), and dropped entries that had missing values. 

### Exploratory Data Analysis (EDA)

* Implemented statistical analysis and visualisations to better understand the dataset.
* Created histograms and box plots to visually represent the distributions of numerical variables and detect any outliers.
* Created a correlation heatmap to analyse the associations among the variables.

### Feature Engineering
* Created interactions phrases, such as the exponential increase of pH and nitrate, to represent a possible combined impact of features.
* Separated numerical features, such as iron level, have been used to represent non-linear correlations.
* Used StandardScaler to normalise numerical features.

### Data Visualization
* Used data visualisation tools to enhance interpretation and display trends in the dataset.
* Created histograms to visually represent the distributions and determine the central tendency of numerical variables.
* Created box plots to identify outliers and analyse the distribution of the data for numerical variables.

## Conclusion:
The dataset provides comprehensive information on water quality indicators and environmental factors. The preliminary review and preprocessing stages simplified data cleansing, handling of missing data, and removing duplicates. The exploratory data analysis provided helpful insights into the distribution of numerical variables and their interrelationships. Data preprocessing techniques were used to optimise the dataset for machine learning models. The in depth report defines the procedures performed to preprocess the data for analysis and provides the foundation for future exploration in predicting water quality.


