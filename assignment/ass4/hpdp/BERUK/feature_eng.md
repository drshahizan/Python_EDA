<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Assignment 4: Feature Engineering


| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
| MUHAMMAD HASAN BIN CHE ABDULLAH | A21EC0077 |Assignment 4 - 100% Contribution|
| HAFIZULSHAH BIN SHAROM | A21EC0027 |Assignment 3| 
| ABDUL MUHAIMIN BIN ABDUL RAZAK | A21EC0002 |Assignment 5|  
| MUHAMMAD HAZIM BIN SALMAN | A21EC0078 |Assignment 5|

## [Google Collab](https://colab.research.google.com/drive/1eAyp3cEGkNs1XR6IwXj7r--DarGQEZaM?usp=sharing)
## Introduction
This project focuses on exploring and applying diverse feature engineering techniques to enhance a dataset containing "Flight Data with 1 Million or More Records" for subsequent machine learning tasks. The primary goal is to prepare the dataset by employing feature engineering methods such as Dimensionality Reduction (PCA), Min-Max Scaling/Preprocessing, Categorical Encoding (Dummy/One-Hot), and Feature Selection. The ultimate aim is to build a predictive model for "price" representing the price of the ticket for the flight's route using linear regression model. The model will leverage various attributes, including duration, flight name, co2_emissions, from/dest_country, aircraft_type, stops, and more.

## Dataset Selection Loading
The dataset is ***[Flight Data with 1 Million or More Records]([https://www.kaggle.com/datasets/polartech/flight-data-with-1-million-or-more-records])*** by [BARKINGDATA] obtained from Kaggle. It is imported locally using Kaggle's API credentials and it is about Global Flight Data Covering top popular airports from Europe, Asia, America, Africa from April to September of the year 2022.

With about 1 million rows of records. Each row contains the following fields:

from_airport_code: Code representing the departure airport.

from_country: Country of the departure airport.

dest_airport_code: Code representing the destination airport.

dest_country: Country of the destination airport.

aircraft_type: Type or model of the aircraft.

airline_number: Numerical identifier for the airline.

airline_name: Name of the airline.

flight_number: Unique identifier for a specific flight.

departure_time: Time when the flight departs.

arrival_time: Time when the flight arrives.

duration: Duration of the flight in a specific unit (e.g., minutes).

stops: Number of stops during the flight.

price: Cost of the flight ticket.

currency: Currency in which the price is specified.

co2_emissions: Amount of carbon dioxide emissions for the flight.

co2_percentage: Percentage of carbon dioxide emissions in relation to the average for the flight route.

scan_date: Date when the flight data was recorded or scanned.

### Data Loading
Install the kaggle python library
```
! pip install kaggle
```
Mount the Google drive so you can store your kaggle API credentials for future use
```
from google.colab import drive
drive.mount('/content/drive')
```
Make a directory for kaggle at the temporary instance location on Colab drive.

Download your kaggle API key (.json file). You can do this by going to your kaggle account page and clicking 'Create new API token' under the API section.
```
! mkdir ~/.kaggle
```
Upload the json file to Google Drive and then copy to the temporary location.
```
!cp /content/drive/MyDrive/Colab_Notebooks/kaggle_API_credentials/kaggle.json ~/.kaggle/kaggle.json
```
Change the file permissions to read/write to the owner only
```
! chmod 600 ~/.kaggle/kaggle.json
```
Download datasets (that are not part of competition)
```
! kaggle datasets download polartech/flight-data-with-1-million-or-more-records
```
Unzip, in case the downloaded file is zipped. Refresh the files on the left hand side to update the view.
```
! unzip flight-data-with-1-million-or-more-records.zip
```
Lastly, load the dataset into Google Collab
```
# Read data
df = pd.read_csv("/content/flight data.csv")
df = df.astype(np.uint8, errors='ignore') # reduce memory footprint
```

## Data Exploration
Before we can do any feature engineering, we need to perform a basic exploratory data analysis to understand the dataset's characteristics. This includes checking for missing values, understanding the data types, and getting a sense of the dataset's structure.

Import the necessary libraries and configurations for feature engineering and EDA
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns
import warnings
from sklearn.cluster import KMeans
from sklearn.feature_selection import mutual_info_regression
from sklearn.preprocessing import MinMaxScaler
from scipy.stats import zscore

plt.style.use("seaborn-whitegrid")
plt.rc("figure", autolayout=True)
plt.rc(
    "axes",
    labelweight="bold",
    labelsize="large",
    titleweight="bold",
    titlesize=14,
    titlepad=10,
)
warnings.filterwarnings('ignore')

```
We'll first find out information on the dataset including data types, null value counts and unique value counts.
```
# rows and columns in the df
df.shape
```
```
df.info()
```
```
class DfOverview:
    """
        Give an overview for a given data frame,
        like null persentage for each columns,
        unique value percentage for each columns and more
    """

    def __init__(self, df: pd.DataFrame) -> None:
        self.df = df

    def missing_value(self) -> None:
        nullSum = self.df.isna().sum()
        return [col for col in nullSum]

    def percentage(self, list):
        return [str(round(((value / self.df.shape[0]) * 100), 2)) + '%' for value in list]

    def getOverview(self) -> None:

        _columns = [column for column in self.df]
        _count = self.df.count().values
        _unique = [self.df[column].value_counts().shape[0] for column in self.df]
        _missing_values = self.missing_value()

        columns = [
            'Column',
            'count',
            'missing_value_count',
            'Missing_value_percentage',
            'unique_value_count',
            'unique_value_percentage',
            'dtype']
        data = zip(
            _columns,
            _count,
            _missing_values,
            self.percentage(_missing_values),
            _unique,
            self.percentage(_unique),
            self.df.dtypes
        )
        new_df = pd.DataFrame(data=data, columns=columns)
        return new_df

# Here we can see detailed informations of the columns including the amount missing and unique values.
df_overview = DfOverview(df)
df_overview.getOverview()
```
-INSERT SS-
```
def show_cols_mixed_dtypes(df):
    mixed_dtypes = {'Column': [], 'Data type': []}
    for col in df.columns:
        dtype = pd.api.types.infer_dtype(df[col])
        if dtype.startswith("mixed"):
            mixed_dtypes['Column'].append(col)
            mixed_dtypes['Data type'].append(dtype)
    if len(mixed_dtypes['Column']) == 0:
        print('None of the columns contain mixed types.')
    else:
        print(pd.DataFrame(mixed_dtypes))

show_cols_mixed_dtypes(df)
```
None of the columns contain mixed types.

## Feature Selection
We then choose the important information for your analysis. You can do this by checking how things are connected, using what you already know, or figuring out which parts matter the most. After deciding, make a new table with only the chosen important parts.
```
# Drop rows with missing values since we have more than enough data points
df = df.dropna()
```
Scikit-learn has two mutual information metrics in its feature_selection module: one for real-valued targets (mutual_info_regression) and one for categorical targets (mutual_info_classif). Our target, price, is real-valued. The next cell computes the MI scores for our features and wraps them up in a nice dataframe.
```
X = df.copy()
y = X.pop("price")

# Label encoding for categoricals
for colname in X.select_dtypes("object"):
    X[colname], _ = X[colname].factorize()

# All discrete features should now have integer dtypes (double-check this before using MI!)
discrete_features = X.dtypes == int

def make_mi_scores(X, y, discrete_features):
    mi_scores = mutual_info_regression(X, y, discrete_features=discrete_features)
    mi_scores = pd.Series(mi_scores, name="MI Scores", index=X.columns)
    mi_scores = mi_scores.sort_values(ascending=False)
    return mi_scores

mi_scores = make_mi_scores(X, y, discrete_features)
mi_scores[::3]  # show a few features with their MI scores
```
We visualise it in a bar-plot for ease of comparison
```
def plot_mi_scores(scores):
    scores = scores.sort_values(ascending=True)
    width = np.arange(len(scores))
    ticks = list(scores.index)
    plt.barh(width, scores)
    plt.yticks(width, ticks)
    plt.title("Mutual Information Scores")


plt.figure(dpi=100, figsize=(8, 5))
plot_mi_scores(mi_scores)
```
-INSERT SS-

Data visualization is a great follow-up to a utility ranking. Let's take a closer look at a couple of these.

We have some surprising finds from these comparisons, namely the relation between price and average/CO2 emissions, stops' and duration's low MI score among others.

currency and scan_date have a 0.0 MI score because both only consist of 1 unique value, which are USD and 29/4/2022 respectively, which also means both fields are not useful enough for our analysis.

If we plot the relation between price and flight number, it wouldn't be suitable as the flight_number in itself does not contain much information other than helpful for instantising specific flights, meaning it has to be modified for it to be useful:
```
sns.relplot(x="flight_number", y="price", hue="stops",  data=df);
```
-INSERT SS-

We can visualise the relationship between avg_co2_emission_for_this_route and price with the aircraft_type as the separating factor. Here we see a noticeable linear correlation between price and avg_co2_emissions_for_this_route. But it might be able to provide clearer information if more variables are taken into account.
```
sns.lmplot(x="avg_co2_emission_for_this_route", y="price", data=df);
# Didn't include hue = aircraft_type or aother columns because google collab could not run it
```
-INSERT SS-

## Feature Engineering
### Preprocessing
#### Min-Max Scaling
Min-Max scaling is a method of standardizing numerical features in a dataset. It transforms the values of the features to a specific range, typically [0, 1], making the features comparable and ensuring they do not dominate each other in terms of scale. We'll apply this to the values 'duration', 'price', 'co2_emissions', 'avg_co2_emission_for_this_route'.
```
numerical_cols = ['duration', 'price', 'co2_emissions', 'avg_co2_emission_for_this_route']

# Create a MinMaxScaler object
scaler = MinMaxScaler()

# Fit the scaler on the selected columns and transform the data
X_minmax = df.copy()

X_minmax[numerical_cols] = scaler.fit_transform(X_minmax[numerical_cols])
```
#### Z-Score Standardisation
Now, on the standardised numerical columns, we can find and remove any outlier values using zscore tool from the scipy library.
```
z_scores = zscore(X_minmax[['duration', 'price', 'co2_emissions', 'avg_co2_emission_for_this_route']])

# Define a threshold for considering data points as outliers (e.g., z_score_threshold = 3)
outliers = (abs(z_scores) > 3).all(axis=1)

# Remove outliers from the DataFrame
X_no_outliers = X_minmax[~outliers]
```

### Transformation
#### Log Transformation
```
selected_columns = ['duration', 'stops', 'price', 'co2_emissions', 'avg_co2_emission_for_this_route']

# Create a figure
fig, axes = plt.subplots(nrows=2, ncols=3, figsize=(18, 10))

# Flatten the axes for easier indexing
axes = axes.flatten()

# Plot histograms for each selected column
for i, col in enumerate(selected_columns):
    X_new[col].plot(kind='hist', ax=axes[i], bins=20, edgecolor='black', color='skyblue')
    axes[i].set_title(f'Histogram of {col}')
    axes[i].set_xlabel(col)
    axes[i].set_ylabel('Frequency')

# Adjust layout
plt.tight_layout()
plt.show()
```
-INSERT SS-
Since for some flights there are multiple trips we can aggregate the rows of same flights to find total duration of flights
```
# Group by specified columns and aggregate
df_aggregated = df.groupby(['price', 'aircraft_type', 'airline_number', 'airline_name', 'flight_number','departure_time', 'arrival_time', 'dest_airport_code', 'from_airport_code', 'stops', 'duration'], as_index=False).agg({
    'from_country': 'first',
    'dest_country': 'first',
    'co2_emissions': 'sum',   # Summing the 'co2_emissions' values
})

df_aggregated.head(10)
```

### Creation
#### One-Hot Encoding
One-Hot Encoding is used on the destination and origin countries of the flights as to separate the countries into separate bins for ease of analysis.
```
X_encoded = pd.get_dummies(X_new, columns=['from_country', 'dest_country'])
X_encoded.head()
```
-INSERT SS-

## Visualisation
### Linear-Regression Model
-INSERT SS-
### K-Means Clustering
-INSERT SS-
### Histogram Comparisons between Pre&Post Logarithmic Transformation
-INSERT SS-
### Bar Chart
-INSERT SS-

## Conclusion
Through the comprehensive application of feature engineering techniques, including data cleaning, handling missing values, encoding categorical variables, and exploring relationships between features, we aimed to enhance the dataset's suitability for predictive modeling. The process involved addressing specific challenges related to the flight data, such as dealing with datetime features, handling categorical variables, and creating relevant new features.

