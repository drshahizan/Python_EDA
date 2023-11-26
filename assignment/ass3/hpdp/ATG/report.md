<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Assignment 3: Exploratory Data Analysis using Big Data

## Profile

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | :-------------:
|Muhammad Iqmal bin Sis | A21EC0080     | Assignment 3
|Sam Chia Yun   |A21EC0127 | Assignment 5
|Aliya Zarena binti Zainulanuar | A21EC0013 |  Assignment 4
|Ang Yi Qin  | A21EC0163  |  Assignment 4


## 📚 Objective 
The objective of this assignment is to perform Exploratory Data Analysis (EDA) on a large dataset using big data tools and techniques. EDA is a tools to help the user understand in details what the data is all about

## 1. Dataset Selection
Our chosen dataset covers airline information from cancellation, delaying and many more.
The dataset that we chose can be retrived through this link [Airline Delay and Cancellation Data-2018](https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018?select=2018.csv).

| Data                | Description                                                   |
|------------------------|---------------------------------------------------------------|
| FL_DATE                | Date of the flight, yy/mm/dd                                  |
| OP_CARRIER             | Airline Identifier                                           |
| OP_CARRIER_FL_NUM      | Flight Number                                                 |
| ORIGIN                 | Starting Airport Code                                        |
| DEST                   | Destination Airport Code                                     |
| CRS_DEP_TIME           | Planned Departure Time                                        |
| DEP_TIME               | Actual Departure Time                                         |
| DEP_DELAY              | Total Delay on Departure in minutes                            |
| TAXI_OUT               | Time duration elapsed between departure and wheels off       |
| WHEELS_OFF             | Time point when the aircraft's wheels leave the ground        |
| WHEELS_ON              | Time point when the aircraft's wheels touch the ground        |
| TAXI_IN                | Time duration elapsed between wheels-on and gate arrival      |
| CRS_ARR_TIME           | Planned arrival time                                          |
| ARR_TIME               | Actual Arrival Time                                           |
| ARR_DELAY              | Total Delay on Arrival in minutes                              |
| CANCELLED              | Flight Cancelled (1 = cancelled)                               |
| CANCELLATION_CODE      | Reason for Cancellation: A - Airline/Carrier; B - Weather; C - National Air System; D - Security |
| DIVERTED               | Aircraft landed on airport that is out of schedule             |
| CRS_ELAPSED_TIME       | Planned time needed for the flight trip                         |
| ACTUAL_ELAPSED_TIME    | AIR_TIME + TAXI_IN + TAXI_OUT                                  |
| AIR_TIME               | Time duration between wheels_off and wheels_on time            |
| DISTANCE               | Distance between two airports                                  |
| CARRIER_DELAY          | Delay caused by the airline in minutes                         |
| WEATHER_DELAY          | Delay caused by weather                                        |
| NAS_DELAY              | Delay caused by air system                                      |
| SECURITY_DELAY         | Delay caused by security                                       |
| LATE_AIRCRAFT_DELAY    | Delay caused by late arrival of the aircraft                    |



## 2. Data Acquisition
The data is conveniently accessible for processing as it is already formatted in CSV.

```
!pip install opendatasets

import opendatasets as od
od.download(
    "https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018?select=2018.csv")
```

The code above shows the usage of Kaggle API in which we implement it inside the collab. The opendatasets library allows us to directly download the dataset from the link. There need to be a verification account for the Kaggle API to works. By doing this it makes it easier for running the whole code and installation part.

## 3. Setting Up the Environment

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import missingno as msno

```
### 3.1 Load the dataset

```
# reading the csv file
file =('airline-delay-and-cancellation-data-2009-2018/2018.csv')
df = pd.read_csv(file)
```
We use the pandas library to read the csv files that has been downloaded using Kaggle API and store it inside the 'df' variable that will be used for the whole analysis

### 3.2 Displaying the general content of the data

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/104277576/d3f4a765-8f34-4801-bc5a-cb0fe01c38a6)

**Figure 1: General Dataset**
</div>

## 4. Data Preprocessing
### 4.1 Missing Values
To check the missing values for each column, we use this code:

```
missing_values = df.isnull().sum()

print("Total missing values for each column:")
print(missing_values)
```
<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/104277576/8ae751c6-2020-44e8-98a4-028884eed13a)

Then we remove it using this code:

```
df.dropna(inplace=True)
```

**Figure 2: Missing Values for each columns**
</div>

### 4.2 Removing Null Columns and Unnecessary Columns

We noticed that there exist various a few columns where it only has null values and also some columns with unnecessary information.
We use the code below to check it:

```
df.info
```
<div align="center"> 
  
![image](https://github.com/drshahizan/Python_EDA/assets/104277576/4b896a91-5d97-4486-aa39-f99f49ad57a6)

**Figure 3: Dataset Info**
</div>

Then we decided to remove :-
  * DIVERTED
  * CANCELLATION_CODE
  * CARRIER_DELAY
  * WEATHER_DELAY
  * NAS_DELAY
  * SECURITY_DELAY
  * LATE_AIRCRAFT_DELAY
  * Unnamed: 27
  * CANCELLED

```
# List of columns to drop
columns_to_drop = ['DIVERTED','CANCELLATION_CODE', 'CARRIER_DELAY', 'WEATHER_DELAY', 'NAS_DELAY', 'SECURITY_DELAY', 'LATE_AIRCRAFT_DELAY', 'Unnamed: 27', 'CANCELLED']

# Drop the specified columns
df.drop(columns=columns_to_drop, inplace=True)
```

```
# to check the shape of the data
df.shape
```

<div align="center"> 
  
![image](https://github.com/drshahizan/Python_EDA/assets/104277576/3d707def-0c3a-4526-83d1-579d02aa1fda)

**Figure 4: Rows and Columns**
</div>

## 5. Exploratory Data Analysis

### 5.1 Summary Statistics

To check the summary of the code; to count how many unique values for each columns, missing values, the percentage of missing and unique values, and their datatype. Below are the code usage of it:

```
class DfOverview:
    """
    Give an overview for a given data frame,
    including missing value, unique value, count,
    data type, percentage, and basic statistics for relevant numerical variables.
    """

    def __init__(self, df: pd.DataFrame) -> None:
        self.df = df

    def missing_value(self) -> list:
        null_sum = self.df.isna().sum()
        return null_sum.tolist()

    def percentage(self, values: list) -> list:
        return [f"{round((value / self.df.shape[0]) * 100, 2)}%" for value in values]

    def compute_basic_statistics(self) -> pd.DataFrame:
        numerical_columns = self.df.select_dtypes(include=['number']).columns
        basic_statistics = self.df[numerical_columns].describe().transpose()
        basic_statistics['median'] = self.df[numerical_columns].median()
        basic_statistics['25th percentile'] = self.df[numerical_columns].quantile(0.25)
        basic_statistics['75th percentile'] = self.df[numerical_columns].quantile(0.75)
        return basic_statistics

    def getOverview(self) -> pd.DataFrame:
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
```

```
# The output of it
df_overview = DfOverview(df)
df_overview.getOverview()
```
<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/104277576/dee83591-1911-4602-9583-59830a93b81f)

**Figure 5: Summary of the data**
</div>

Next, we calculate all the mathematical standard such as;  mean, median, standard deviation, and quantiles for relevant numerical variables.

Below are the code where we calculate it

```
pd.options.display.float_format = '{:.4f}'.format
numerical_columns = df.select_dtypes(include='number').columns
statistics = df[numerical_columns].describe()
statistics
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/104277576/78704463-4a02-4a7e-99ad-04d6cc1b6cd3)

**Figure 6: Statistics of the data**
</div>

### 5.2 Data Visualization

#### 5.2.1 Histogram

The histogram use the duration of the airplane fly (AIR_TIME) with the frequency of it
```
plt.figure(figsize=(12, 8))

# Use a different color and adjust edgecolor
df['AIR_TIME'].hist(bins=30, color='skyblue', edgecolor='white')

plt.title('Distribution of Air Time')
plt.xlabel('Air time')
plt.ylabel('Frequency')
plt.grid(axis='y', linestyle='--', alpha=0.7)  # Add grid lines for better readability
plt.show()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/104277576/e40a3b7c-de14-467c-a638-22e9ee4f51c0)


**Figure 7: Histogram of Air Time**
</div>

#### 5.2.2 Box Plot

The box plot shows the total delay of departure and each airplane

```
plt.figure(figsize=(16, 10))
sns.boxplot(x='OP_CARRIER', y='DEP_DELAY', data=df, showfliers=False)
plt.title('Box Plot of DEP_DELAY by OP_CARRIER')
plt.xlabel('OP_CARRIER')
plt.ylabel('DEP_DELAY')
plt.show()
```
<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/104277576/eb690968-5df7-49ca-83f6-aec7ccadd287)

**Figure 8: Boxplot of Total Delay Departure for each airplane**
</div>

#### 5.2.3 Scatter Plot

The scatter plot shows the total distance and their air time

```
plt.figure(figsize=(12, 8))

# Set a specific color for all points
sns.scatterplot(x='DISTANCE', y='AIR_TIME', data=df, color='red', alpha=0.7)

plt.title('Scatter Plot of AIR_TIME by DISTANCE')
plt.xlabel('DISTANCE')
plt.ylabel('AIR_TIME')
plt.show()
```
<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/104277576/d5883be6-48fc-4d32-bea8-a31f0dc033dd)

**Figure 9: Scatterplot for total distance and airtime**
</div>

#### 5.2.4 Heatmap Correlation

The heatmap shows the correlation for each columns

```
correlation_matrix = df.corr()

plt.figure(figsize=(12, 8))
sns.heatmap(correlation_matrix, annot=True, cmap='Reds', linewidths=.5)
plt.title('Correlation Heatmap')
plt.show()
```
<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/104277576/5432716a-8bc4-4511-9a3d-83f21300141c)

**Figure 10: Heatmap for each columns**
</div>

#### 5.2.5 Pie Chart

The pie chart shows the Airline Distribution 

```
plt.figure(figsize=(12, 8))

# Choose a darker color palette for the pie chart
colors = plt.cm.Set1.colors

# Plot the pie chart
pie_chart = df['OP_CARRIER'].value_counts().plot.pie(autopct='%1.1f%%', colors=colors)

# Move the legend outside the pie chart
plt.legend(bbox_to_anchor=(1, 1), loc='upper left')

# Add a title to the chart
plt.title('Airline Distribution')

# Ensure that text does not spill out of the pie chart
plt.tight_layout()

# Show the pie chart
plt.show()
```
<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/104277576/a28bc8a9-deee-4f1e-aa5c-136e0ea1f0c3)

**Figure 11: Pie Chart for Airplane Distribution**
</div>

### 5.3 Data Exploration

#### 5.3.1 Histogram for each columns

```
import math

# Assuming 'df' is your DataFrame with numerical variables
numerical_columns = df.select_dtypes(include='number').columns

# Calculate the number of rows needed
num_rows = math.ceil(len(numerical_columns) / 5)

# Set up subplots with 5 columns
fig, axes = plt.subplots(nrows=num_rows, ncols=5, figsize=(15, 3 * num_rows))

# Flatten the axes array to simplify indexing
axes = axes.flatten()

# Plot histograms for each numerical variable
for i, column in enumerate(numerical_columns):
    df[column].plot(kind='hist', ax=axes[i], bins=30, edgecolor='black', color='skyblue')
    axes[i].set_title(f'Histogram of {column}')
    axes[i].set_xlabel(column)
    axes[i].set_ylabel('Frequency')

# Remove any empty subplots
for j in range(len(numerical_columns), len(axes)):
    fig.delaxes(axes[j])

# Adjust layout
plt.tight_layout()

# Show the histograms
plt.show()

```
<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/104277576/122c11f6-c368-4da8-a1f5-fd0f4e68d69c)

**Figure 12: histogram for each column**
</div>

#### 5.3.2 Data Exploration Conclusion

From the histogram, we can conclude that:

* Actual Elapsed time with the highest peak is around 1.3×10⁶
* There are almost no delay in departure
* There are also almost no delay in arrival 

From the Heatmap, we can conclude that:

* The air time (duration of wheels on and off) and crs_elapsed_time (planned time for needed trip) and actual_elapsed_time got a 0.99 correlation. This shows that both variable highly related and the plane follow the whole procedure of it

From the boxplot, we can conclude that:

* Plane F9 has an outlier or extreme values exceeding 60mins. What it meant is that the plane has a record of departure delay for more than 1 hours.

### 5.4 Feature Engineering

#### 5.4.1 Creating Feature: Departure Hour

Create a new feature representing the hour of the day the flight departs. This can capture potential patterns related to the time of day.

```
df['DEP_HOUR'] = pd.to_datetime(df['DEP_TIME'], format='%H:%M', errors='coerce').dt.hour
```
This code creates a new feature 'DEP_HOUR' representing the hour of the day when the flight departs. It converts the 'DEP_TIME' column to a datetime format and extracts the hour.

#### 5.4.2 Creating Feature: Flight Duration Deviation

Create a feature that represents the deviation of the actual flight duration from the planned duration.

```
# Assuming 'df' is your DataFrame with the flight data
df['DURATION_DEVIATION'] = df['ACTUAL_ELAPSED_TIME'] - df['CRS_ELAPSED_TIME']
```

This code creates a new feature 'DURATION_DEVIATION' that represents the difference between the actual elapsed time and the planned elapsed time. This can provide insights into how closely actual flight durations align with the scheduled durations.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)














