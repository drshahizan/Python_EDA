# Assignment 4:Feature Engineering (Report)
## Group members
| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
|MUHAMMAD AMIR JAMIL BIN JAMLUS          | A21EC0202     | Main Code(Preprocess, EDA , Feature Engineering)  , Report |
|KEE SHIN PEARL         | A21EC0190     | Verify   |
|MUHAMMAD IZZUDDIN BIN SHABRIN           | A21EC0083   | Verify    |
|UMAR HAZIQ BIN MUHAMAD NORHISHAM            |  A21EC0235   | Finding data     |

## Introduction
The purpose of this project is to learn and utilize various feature engineering techniques. In this particular project, we utilized feature engineering technique on a dataset of "Spotify 1 million tracks" to further prepare the dataset for machine learning tasks. Here, in order for us to perform machine learning tasks we first need to apply feature engineering techniques such as ***Dimensionality Reduction (PCA), Scaling / Preprocessing, Categorical Encoding (Dummy / One-Hot), Binning (Grouping, Aggregating), and lastly Feature Selection***. When we apply all these feature engineering techniques we will observe the ***mean_absolute_error*** value of the dataset and the predictions to decide which technique or which combinations of techniques produce the best result for our machine learning predictions. The prediction will predict the popularity based on various different attributes such as ***genre, danceability, acoustics, speechiness, loudness, energy, duration, insturmentals and so on***

## Data Loading
The dataset is ***[Spotify_1_million_tracks](https://www.kaggle.com/datasets/amitanshjoshi/spotify-1million-tracks/data)*** obtained from Kaggle. It is imported locally and it is about the 1 million list of songs uploaded to spotify with various attributes like ***artist, year, song_id, genre, danceability, acoustics, speechiness, loudness, energy, duration, insturmentals and so on***. The dataset has around 1100000 rows and 16 rows with various python datatypes such as object and int64.


## Feature Engineering
### Dimensionality Reduction (PCA)
Dimensionality reduction is a crucial step in machine learning to simplify the dataset while retaining essential information. This report explores the application of Principal Component Analysis (PCA) for dimensionality reduction on a subset of features, namely 'danceability', 'energy', and 'loudness', and evaluates its impact on a RandomForestRegressor model. We started by examining the correlation matrix for the selected features.

  - Correlation Analysis: Investigated the correlation matrix of selected features ('danceability', 'energy', 'loudness').
  - Feature Selection: Prepared the data for dimensionality reduction.
  - Baseline Model: Trained a RandomForestRegressor as a baseline model.
  - Principal Component Analysis (PCA): Applied PCA for dimensionality reduction.
  - Model with Reduced Dimensions: Trained a model using reduced dimensions and evaluated its performance.

<img width="389" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/bb618338-ff85-46ec-b9c4-a7b30beac293">


In conclusion, the dimensionality reduction using PCA was applied to the features 'danceability', 'energy', and 'loudness'. The performance of a RandomForestRegressor model was evaluated with both the baseline features and the reduced dimensions. The mean absolute error metrics provide insights into the impact of dimensionality reduction on model performance.

### Scaling
Scaling and dimensionality reduction are essential preprocessing steps in machine learning. This report explores the application of scaling techniques and Principal Component Analysis (PCA) for dimensionality reduction on a subset of features ('danceability', 'energy', 'loudness') and evaluates their impact on RandomForestRegressor models.

  - Standard Scaling: Scaled numerical features using StandardScaler.
  - Visualization: Explored the impact of scaling on the distribution of features.
  - Model with Scaled Features: Trained a RandomForestRegressor using scaled features and evaluated its performance.


<img width="390" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/fe3bcf8d-08f6-45bc-82b9-f1ee52b9cc34">

In conclusion, the application of Standard Scaling was explored for the features 'danceability', 'energy', and 'loudness'. A RandomForestRegressor model was trained using the scaled features, and its performance was evaluated. The mean absolute error provides insights into the impact of scaling on model performance.

### Categorical Encoding 
Categorical encoding is a crucial step in handling categorical variables in machine learning models. This report explores the application of dummy encoding (one-hot encoding) on the 'genre' feature and evaluates its impact on a Linear Regression model.

  - Dummy Encoding (One-Hot Encoding): Applied dummy encoding to the 'genre' feature.
  - Model with Encoded Features: Trained a Linear Regression model using encoded categorical features and evaluated its performance.
    
<img width="395" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/c6ee731a-69f9-414b-bc59-0d46daaada28">

In conclusion, dummy encoding was applied to the 'genre' feature, creating binary columns for each category. A Linear Regression model was trained using the encoded features, and its performance was evaluated. The mean absolute error provides insights into the impact of categorical encoding on model performance.

### Binning (Grouping, Aggregating)
Binning, also known as grouping or aggregating, is a technique used to transform continuous numerical data into discrete bins. This report explores the application of binning to the 'tempo' feature by creating a binary indicator based on a specified threshold and evaluates its impact on a Linear Regression model.

  - Binning Based on Tempo: Created a binary indicator based on a specified threshold for the 'tempo' feature.
  - Model with Binned Feature: Trained a Linear Regression model using the binned 'tempo' feature and evaluated its performance.

<img width="437" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/b57a93bd-9a5e-4422-8faa-1a3da50d998b">


In conclusion, binning was applied to the 'tempo' feature by creating a binary indicator based on a specified threshold. A Linear Regression model was trained using the binned feature, and its performance was evaluated. The mean absolute error provides insights into the impact of binning on model performance.


### Feature Selection
Feature selection is a critical step in machine learning to choose relevant features for model training. This report explores the application of feature selection by combining scaled numerical features and dummy-encoded categorical features and evaluates its impact on a RandomForestRegressor model.

  - Combining Features: Combined scaled numerical and dummy-encoded categorical features.
  - Model with Selected Features: Trained a RandomForestRegressor using selected features and evaluated its performance.


<img width="523" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/3fc8d0b0-bc41-42bb-b17b-94433efcb414">


In conclusion, feature selection was performed by combining scaled numerical features and dummy-encoded categorical features into a single feature matrix. A RandomForestRegressor model was trained using the selected features, and its performance was evaluated. The mean absolute error provides insights into the impact of feature selection on model performance.


## Data Exploration
The following visualizations and analyses explore the dataset and its features:

  - Correlation heatmap
  - Pair Plot
  - Genre Counts Bar Chart
  - Average Popularity by Genre Bar Chart
  - Average Popularity by Genre Bar Chart (Filtered)

<img width="428" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/c467b8da-ca20-49d3-a45a-42fd8dc95e63">
<img width="623" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/9f17c49e-b83e-491d-834e-499abbbce06a">
<img width="363" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/a1fa6512-4339-47da-895c-26f0a8ed4023">
<img width="353" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/b39870ea-29fa-404d-bab1-606bf45704c0">
<img width="350" alt="image" src="https://github.com/drshahizan/Python_EDA/assets/146797903/fd2f035e-a150-4b77-a318-dd62c3511e85">




## Conclusion
Feature Selection: Among all the preprocessing techniques, the RandomForestRegressor model trained on the combined features produced the lowest mean absolute error (MAE) value. This indicates that the process of selecting and combining features contributed to improved model performance.
In conclusion, the application of these preprocessing techniques is context-dependent, and the optimal choice may vary based on the specific characteristics of the dataset and the goals of the machine learning task. Further fine-tuning and experimentation can provide deeper insights into the most effective preprocessing strategies.
