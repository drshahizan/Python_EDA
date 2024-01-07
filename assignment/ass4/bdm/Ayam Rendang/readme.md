<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# Assignment 4: Feature Engineering

### Group Name: Ayam Rendang
### Group Members

| Name          | Matric Number  | 
| ------------- | -------------- | 
| NURUL WAHIEDA BINTI MUHAMMAD FARID SELLEKUMAR   | (MCS231022)     |
|THANEATHARRAN A/L SANTHARASEKARAN    | (MSC232006)       | 
| RANJEET A/L THIAGARAJAN   | (MCS231015)         | 
| LINGGESH A/L TAMILMANI   | (MCS232005)         | 

## Assignment Link
* [📖 Google Colab link ](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass4/bdm/Ayam%20Rendang/Assignment%204%20(Ayam%20Rendang)%20-%20Feature_Engineering.ipynb)

## Dataset: Predict Diabetes
This dataset is originally from the National Institute of Diabetes and Digestive and Kidney Diseases. The objective of the dataset is to diagnostically predict whether a patient has diabetes, based on certain diagnostic measurements included in the dataset. Several constraints were placed on the selection of these instances from a larger database. In particular, all patients here are females at least 21 years old of Pima Indian heritage.

### Task Overview
This assignment explores the essential concept of feature engineering in data science. Feature engineering is a critical step in the data preprocessing process, where you manipulate and create new features from your dataset to improve the performance of machine learning models.

Below shows the steps in feature engineering
1. **Dataset Selection**: Your first task is to select a suitable dataset for this assignment. You can choose a dataset from various sources, such as Kaggle, UCI Machine Learning Repository, or any other relevant dataset source. Make sure the dataset is in a format that can be easily loaded into Google Colab.

2. **Loading the Dataset**: Use Python libraries like Pandas to load the selected dataset into your Colab notebook. You can upload the dataset from your local machine or load it directly from an online source.

3. **Exploratory Data Analysis (EDA)**: Perform a basic exploratory data analysis to understand the dataset's characteristics. This includes checking for missing values, understanding the data types, and getting a sense of the dataset's structure.

4. **Feature Selection**: Identify which features are relevant for your analysis. You can use techniques like correlation analysis, domain knowledge, or feature importance to choose the most important features. Create a new DataFrame containing only the selected features.

5. **Feature Preprocessing**: Clean the selected features as needed. This may include handling missing values, dealing with outliers, and standardizing or normalizing data.

6. **Feature Transformation**: Apply transformations to the selected features. You can use techniques like one-hot encoding for categorical features, logarithmic transformations for skewed data, or any other relevant transformations to make the data suitable for modeling.

7. **Feature Creation**: Create new features if they can provide valuable information. This could involve combining or aggregating existing features or engineering new ones based on domain knowledge.

8. **Visualization**: Visualize the transformed data to gain insights into feature distributions and relationships.

### Conclusion

#### Key Findings:

1. Dataset Overview:
  - The diabetes dataset comprises information on health metrics and patient details, including features like 'Glucose,' 'BMI,' and 'Age.'
2. Exploratory Data Analysis (EDA):
  -Checked for missing values: Identified that 'Glucose' had missing values, requiring further attention.
  - Examined data types and statistics: Observed that 'Glucose' exhibited right-skewness in its distribution.
3. Feature Selection:
  - Utilized correlation analysis: Found that 'BMI' and 'Age' are moderately correlated with the target variable.
  - Domain knowledge: Recognized the importance of 'Glucose' in diabetes-related analyses.
4. Feature Preprocessing:
  - Handled missing values: Imputed missing 'Glucose' values using the mean or median.
  - Addressed outliers: Detected and treated outliers in 'BMI' using appropriate methods.
5. Feature Transformation:
  - Applied logarithmic transformations: Addressed skewness in 'Glucose' by applying a logarithmic transformation.
6. Feature Creation:
  - Introduced a new feature, 'Avg_Age_Pregnancies':
  - Computed as the average of 'Age' and 'Pregnancies' for each patient.
7. Visualization:
  - Created visualizations:
  - Box plot for 'BMI' after outlier treatment.
  - Distribution plot for 'Glucose' before and after logarithmic transformation.
#### Insights:
Imputing missing values and treating outliers improved the overall quality of the dataset.
Logarithmic transformation on 'Glucose' effectively addressed its right-skewed distribution.
The newly created feature, 'Avg_Age_Pregnancies,' offers a combined metric capturing both age and pregnancy history.

#### Future Steps:
Further exploration could involve additional feature engineering techniques tailored to the characteristics of specific variables.
Continuous monitoring and refinement of feature engineering strategies based on model performance and domain insights.
By systematically addressing challenges and enhancing features, we've prepared the diabetes dataset for more robust and meaningful machine learning analyses.
