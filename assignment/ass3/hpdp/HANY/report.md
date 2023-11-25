<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Assignment 3: Exploratory Data Analysis using Big Data

### Group Name: HANY
### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | :-------------: |
| LIEW YVONNE            |A21EC0045      | Assignment 3 |
| NADIA SYAFIQAH BINTI ZULKIPLI  | A21EC0098      | Assignment 3 |
| ALYA BALQISS BINTI AZAHAR   |  A21EC0158     | Assignment 4 |
| MUHAMMAD HARITH HAKIM BIN OTHMAN              | A21EC0205     | Assignment 4|

## 📚 Objective 
The objective of this assignment is to perform Exploratory Data Analysis (EDA) on a large dataset using big data tools and techniques. EDA is a critical step in understanding the characteristics of a dataset and uncovering insights that can inform further analysis and decision-making.

## 1. Dataset Selection
Our chosen dataset covers hourly weather data from 623 inmet weathers stations of Brazil.
The dataset that we chose can be retrived through this link [Climate Weather Surface of Brazil - Hourly](https://www.kaggle.com/datasets/PROPPG-PPG/hourly-weather-surface-brazil-southeast-region).

## 2. Data Acquisition
The data is conveniently accessible for processing as it is already formatted in CSV.

## 3. Setting Up the Environment
### Import the necessary libraries
```
import numpy as np
import pandas as pd
import gc
import glob
import os

import random
from sys import getsizeof

import matplotlib.pyplot as plt
import seaborn as sns
```

### 3.1. Load the Dataset
Here are the methods for directly accessing datasets from Kaggle:

1. Login to your [kaggle.com](www.kaggle.com) account.
2. On the top right of the page, you can see your profile. Click on the profile, you will then see an option to view **Your Profile**, **Settings** and **Sign Out**.
3. Click on the **Settings** button, which is indicated by a gear icon.
<div align="center">
  
![img1](https://github.com/drshahizan/Python_EDA/assets/87573002/a88de648-099c-4ef0-915a-472de81b0147)
  
**Figure 1: Display your Kaggle Account.**
</div>

4. On your account page, scroll down until you see an API section. Click on the **Create New Token** as shown in Figure 2 below.
<div align="center">
  
![img2](https://github.com/drshahizan/Python_EDA/assets/87573002/84ab6dc3-5ff3-4b05-a96b-8ace6019d13c)

**Figure 2: Display your Account Settings.**
</div>

5. You will then be given a JSON file named kaggle.json, which contains the API Key, which is unique to your account and must not be shared.
6. Upload the **kaggle.json** file on Google Drive.
<div align="center">
  
![img3](https://github.com/drshahizan/Python_EDA/assets/87573002/12c1cd3d-b621-43d1-947c-8aa19086f24c)
**Figure 3: Display the uploaded kaggle.json file into Drive.**
</div>

7. After the file have been uploaded, use the following command to mount your drive storage on your new colab notebook:

```
from google.colab import drive
drive.mount('/content/drive')
```

8. You will be requested to grant access to your drive storage by selecting your preferred account.
<div align="center">
  
![img4](https://github.com/drshahizan/Python_EDA/assets/87573002/f25f425a-e87e-4874-8d72-947c73b7a15d)

**Figure 4: Displays the pop-up permission.**
</div>

9. Install the required libraries and run the below script :
```
!pip install -q kaggle
!pip install -q kaggle-cli
```

```
!mkdir -p ~/.kaggle
!cp "/content/drive/MyDrive/kaggle.json" ~/.kaggle/
!cat ~/.kaggle/kaggle.json
!chmod 600 ~/.kaggle/kaggle.json
```
10. To access the dataset, run the following command:
• Copy the link after **dataset** keyword.
<div align="center">
  
![img5](https://github.com/drshahizan/Python_EDA/assets/87573002/dd0da122-262d-4285-bd92-5a545586c7d5)
**Figure 5: Shows the dataset link.**
</div>

```
!kaggle datasets download -d PROPPG-PPG/hourly-weather-surface-brazil-southeast-region
```
• Extract the file contents by using this command:
```
!unzip /content/hourly-weather-surface-brazil-southeast-region.zip
```
  This output messages will be appeared on your screen as shown in Figure 6.
  <div align="center">
    
  ![img6](https://github.com/drshahizan/Python_EDA/assets/87573002/c21a07dc-887a-4898-8f9b-d0102e3acbe5)
  
  **Figure 6: Shows the output messages in Colab Notebook.**
</div>

### 3.2. Chunking
This technique will split selected file into smaller pieces called chunks by using the chunking algorithm. If you are working with a huge amount of data, retrieving a large dataset all at once can consume a lot of RAM. Hence, by using the chunk method, we can process the data into smaller chunks which can be more memory efficient.

• Run the following command:
```
chunk_size = 5000
num = 1
for chunk in pd.read_csv('central_west.csv', chunksize=chunk_size):
  chunk.to_csv('chunk'+str(num)+'.csv', index=False)
  gc.collect()
  num+=1
```

• Read the chunk file and review its information.
```
df = pd.read_csv('chunk2.csv')
df.head()
```
This will displays the first 5 rows in the dataframe as shown in Figure 7 below.
<div align="center">
   
![img7](https://github.com/drshahizan/Python_EDA/assets/87573002/74627d94-e9d7-4b1d-9112-a36fa944ecd8)

**Figure 7: Shows the output messages in Colab Notebook.**
</div>

### 3.3. Optimise memory of dataset
Review the dataframe information includes the data types.
```
df.info()
```
<div align="center">
  
![img8](https://github.com/drshahizan/Python_EDA/assets/87573002/3e38f947-119e-4e0a-ba88-8fc714962dda)

**Figure 8: Displays the dataframe information.**
</div>

One of the most common problems with pandas is that it constantly loads float data as **float64**. By optimizing the memory, we could have reduced a part of the memory from our dataset. Here, we will converting float64 to **float16** or **float32** to minise memory usage.
```
for column in df.columns:
  if df[column].dtype == 'float64':
    df[column] = df[column].astype('float16')
  if df[column].dtype == 'int64':
    df[column] = df[column].astype('int16')
```

• To compare the memory usage, run the following code:
```
df.info()
```
<div align="center">
  
![img9](https://github.com/drshahizan/Python_EDA/assets/87573002/1fdd1b56-89de-4010-809d-a5ccece958c8)

**Figure 9: Displays the dataframe information.**
</div>
From the above Figure 9, we can know that the memory usage has been reduced to 439.6+ KB from 1.0+ MB. But this is only for one chunk file.

<br><br>
Now we are going to contact all chunk files and optimize the memory as well.
```
path = 'central_west.csv'
all_files = glob.glob(os.path.join(path, "*.csv"))
grouped_files = []

for filename in all_files:
  chunk = pd.read_csv(filename, index_col=None, header=0)
  for col in chunk.columns:
    if chunk[col].dtype == 'float64':
      chunk[col] = chunk[col].astype('float16')
    if chunk[col].dtype == 'int64':
        chunk[col] = chunk[col].astype('int8')
  gc.collect()
  grouped_files.append(chunk)

  df = pd.concat(grouped_files, axis=0, ignore_index=True)
```
```
df.info()
```
<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/20b0d39f-b890-4a9e-9736-e29df5b4eae7)

**Figure 10:**

</div>

```
df.to_csv("central_west_1.csv")
```
```
df = pd.read_csv('central_west_1.csv')
df.head()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/2d58e607-5d05-4af3-94d0-70bae18c5975)

**Figure 11:**

</div>

### 3.4Rename columns name
The used dataset are basically in Portuguese. We can see by displaying the column names in the dataframe below.
```
#df = pd.read_csv('central_west.csv')
print(df.columns) #Display the current column names in dataframe
```

<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/106257072/f6216be2-6d83-491f-bc71-ac0c43182c22)

**Figure 12: Column Names in Portuguese**

</div>

Change all the column names to English.

• To change all column names to English:
```
column_mapping = {
    'Data': 'Date',
    'Hora': 'Time',
    'PRECIPITAÇÃO TOTAL, HORÁRIO (mm)': 'Amount of precipitation, last hour (mm)',
    'PRESSAO ATMOSFERICA AO NIVEL DA ESTACAO, HORARIA (mB)': 'Atmospheric pressure at station level (mB)',
    'PRESSÃO ATMOSFERICA MAX.NA HORA ANT. (AUT) (mB)': 'Maximum air pressure for the last hour (mB)',
    'PRESSÃO ATMOSFERICA MIN. NA HORA ANT. (AUT) (mB)': 'Minimum air pressure for the last hour (mB)',
    'RADIACAO GLOBAL (Kj/m²)': 'Solar radiation (Kj/m²)',
    'TEMPERATURA DO AR - BULBO SECO, HORARIA (°C)': 'Air temperature (instant) (°C)',
    'TEMPERATURA DO PONTO DE ORVALHO (°C)': 'Dew point temperature (instant) (°C)',
    'TEMPERATURA MÁXIMA NA HORA ANT. (AUT) (°C)': 'Maximum temperature for the last hour (°C)',
    'TEMPERATURA MÍNIMA NA HORA ANT. (AUT) (°C)': 'Minimum temperature for the last hour (°C)',
    'TEMPERATURA ORVALHO MAX. NA HORA ANT. (AUT) (°C)': 'Maximum dew point temperature for the last hour (°C)',
    'TEMPERATURA ORVALHO MIN. NA HORA ANT. (AUT) (°C)': 'Minimum dew point temperature for the last hour (°C)',
    'UMIDADE REL. MAX. NA HORA ANT. (AUT) (%)': 'Maximum relative humidity for the last hour (%)',
    'UMIDADE REL. MIN. NA HORA ANT. (AUT) (%)': 'Minimum relative humidity for the last hour (%)',
    'UMIDADE RELATIVA DO AR, HORARIA (%)': 'Relative humidity (% instant)',
    'VENTO, DIREÇÃO HORARIA (gr) (° (gr))': 'Wind direction (radius degrees (0-360))',
    'VENTO, RAJADA MAXIMA (m/s)': 'Wind gust (m/s)',
    'VENTO, VELOCIDADE HORARIA (m/s)': 'Wind speed (m/s)',
    'region': 'Brazilian geopolitical regions',
    'state': 'State (Province)',
    'station': 'Station Name (usually city location or nickname)',
    'station_code': 'Station code (INMET number)',
    'latitude': 'Latitude',
    'longitude': 'Longitude',
    'height': 'Elevation'
}

```
```
df.rename(columns=column_mapping, inplace=True)
```
• When you run this command, you can see that all of the column already changed.

```
print(df.columns)
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/10fe8ccc-c084-4adb-8996-79dcefb97b89)

**Figure 13: Column Names Changed to English**

</div>

As we can see, all of the columns have been renamed to English.

### 3.5 Optimise data types

• To calculate initial size of dataframe, run the following code:
```
%pylab inline
```

```
start_size = getsizeof(df)/(1023.0**3)
print('Dataframe size: %2.2f GB'%start_size)
```

```
df.dtypes
```
<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/106257072/0f8a8b3a-b86a-425f-be51-b749c70dc4b0)

**Figure 14: Original Data Types of All Column**

</div>

Next, we will also convert:

  a) Integer Columns
  ```
#Convert integer columns to smaller integer types if applicable
int_cols = ['Solar radiation (Kj/m²)', 'Maximum relative humidity for the last hour (%)',
                'Minimum relative humidity for the last hour (%)', 'Relative humidity (% instant)',
                'Wind direction (radius degrees (0-360))']

df[int_cols] = df[int_cols].apply(pd.to_numeric, downcast='integer')
  ```

  b) Float Columns
  ```
#Convert float columns to smaller float types if applicable
float_cols = ['Amount of precipitation, last hour (mm)', 'Atmospheric pressure at station level (mB)',
              'Maximum air pressure for the last hour (mB)', 'Minimum air pressure for the last hour (mB)',
              'Air temperature (instant) (°C)', 'Dew point temperature (instant) (°C)',
              'Maximum temperature for the last hour (°C)', 'Minimum temperature for the last hour (°C)',
              'Maximum dew point temperature for the last hour (°C)', 'Minimum dew point temperature for the last hour (°C)',
              'Wind gust (m/s)', 'Wind speed (m/s)', 'Latitude', 'Longitude', 'Elevation']  # List of float columns to optimize

df[float_cols] = df[float_cols].apply(pd.to_numeric, downcast='float')
  ```

  c) Object columns to Category.
```
#Convert object columns to category if suitable
object_cols = ['Brazilian geopolitical regions', 'State (Province)', 'Station Name (usually city location or nickname)',
               'Station code (INMET number)']  # List of object columns to optimize

for col in object_cols:
    if df[col].nunique() / len(df[col]) < 0.5:  # Adjust the threshold based on your data
        df[col] = df[col].astype('category')
```

```
#Convert object columns to category if suitable
object_cols = ['Date', 'Time']  # List of object columns to optimize

for col in object_cols:
    if df[col].nunique() / len(df[col]) < 0.5:  # Adjust the threshold based on your data
        df[col] = df[col].astype('category')
```
  d) Date and Time columns to datetime.
  
  Since the Pandas stores Date and Time columns as datetime objects, which can take more memory due to their internal representation as timestaps, we will try to convert Date and Time columns to Category data type.
  
```
df['Date'] = pd.to_datetime(df['Date'], format='%Y-%m-%d').dt.date
df['Time'] = pd.to_datetime(df['Time'], format='%H:%M').dt.time
```

When we try to convert date and time to datetime format, Pandas stores them as datetime objects, which can take more memory due to their internal representation as timestamps. Datetime objects store both date and time information with higher precision, resulting in larger memory usage compared to categorical data.


• To calculate total size of reduction, run the following code:
```
final_size = getsizeof(df)/(1024**3)
print('Dataframe size: %2.2f GB'%final_size)
```
```
print('Total size reduction: %2.1f'%((1-final_size/start_size)*100))
```

<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/106257072/30e792d8-accd-451b-98e5-19af2a1da3da)

**Figure 15: Total Size Reduction**

</div>

From Figure 15, we can see that the total size reduction is 82.5

```
df.dtypes #Check the optimized data types after conversion
```


<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/106257072/9540cf60-4322-4195-9b1e-eb0e693d537b)


**Figure 16: Final Data Types of All Column**

</div>



## 4. Data Preprocessing
### Missing Values
Check for the missing values by using this command:
```
def percent_missing_values(df):

    # Calculate total number of cells in dataframe
    totalCells = np.product(df.shape)

    # Count number of missing values per column
    missingCount = df.isnull().sum()

    # Calculate total number of missing values
    totalMissing = missingCount.sum()

    # Calculate percentage of missing values
    print("The dataset contains", round(((totalMissing/totalCells) * 100), 2), "%", "missing values.")
```

```
percent_missing_values(df)
```
<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/106257072/e8e08778-7d8c-4d54-922d-52333a46efcc)

**Figure 17: Percentage of Missing Values**

</div>

Since the dataset did not contain any missing values, we can proceed with the next steps.

### Removing Duplicates
This command will be functioning to find any duplicates row and removed them.
```
def drop_duplicates(df):
    old = df.shape[0]
    df.drop_duplicates(inplace=True)
    new = df.shape[0]
    count = old - new
    if (count == 0):
        print("No duplicate rows were found.")
    else:
        print(f"{count} duplicate rows were found and removed.")
```
• Search for duplicate rows and drop them
```
drop_duplicates(df)
```
<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/8d35d00a-a99f-4c47-b9b9-de94f69a3c91)

**Figure 18: Output of Removing Duplicates**

</div>

After removing duplicates, there are no more duplicate rows found.

### Replace Extreme Values
Due to the presence of negative values in certain rows, we intend to substitute those specific values with zero.
```
columns_to_replace = ['Maximum air pressure for the last hour (mB)', 'Minimum air pressure for the last hour (mB)', 'Solar radiation (Kj/m²)','Dew point temperature (instant) (°C)', 'Amount of precipitation, last hour (mm)',
                      'Maximum temperature for the last hour (°C)', 'Minimum temperature for the last hour (°C)', 'Maximum dew point temperature for the last hour (°C)',
                      'Minimum dew point temperature for the last hour (°C)', 'Maximum relative humidity for the last hour (%)', 'Minimum relative humidity for the last hour (%)',
                      'Relative humidity (% instant)', 'Wind gust (m/s)', ]

for column in columns_to_replace:
    df[column] = df[column].apply(lambda x: 0 if x < 0 else x)
```

## 5. Exploratory Data Analysis
In this section, we will use big data tools to complete the following EDA tasks.

### General Statistics
• To calculate number of elements in the dataframe:
```
df.size
```
<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/a7913473-557e-4013-b3f6-bc582ecf6744)

**Figure 19: Size in the Dataframe**

</div>

• To count number of rows and columns:
```
df.shape
```
<div align="center">
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/28fff749-a0a9-44b8-9142-2e1cff3d6034)

**Figure 20: Number of rows and columns**

</div>

### Dataframe Overview

• To view the dataframe overview:
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
```

```
df_overview = DfOverview(df)
df_overview.getOverview()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/fecdf6ae-41db-4983-96cd-fb4fb66137f4)


**Figure 21: Overview of Dataframe**

</div>

Here we can see detailed informations of the columns including the amount missing and unique values.

### Summary Statistics
We only use numerical columns to compute basic statistics since it is easier to do mathematical operations and calculations on this type of data.

Run the following command:
```
numerical_columns = df.select_dtypes(include='number').columns
statistics = df[numerical_columns].describe()
statistics
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/c1ebbc3e-0a1c-42da-9cc2-490f3c54c828)

**Figure 22: Summary Statistic of Dataframe**

</div>

The table above summarizes all of the statistics for the relevant numerical variables, such as mean, median, standard deviation, and quantiles.

### Data Visualization
(A) Histogram

This histogram shows the frequency of Amount of Precipitation, last hour in mm.
```
plt.figure(figsize=(8, 6))
sns.histplot(df['Amount of precipitation, last hour (mm)'], kde=True)
plt.title('Histogram of Amount of Precipitation')
plt.xlabel('Amount of precipitation')
plt.ylabel('Frequency')
plt.show()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/a785ed0b-c760-428c-92a6-10d695a09bb3)

**Figure 23: Histogram of Amount of Precipitation**

</div>

From Figure 23, the amount of precipitation land mostly between 0-5.

(B) Bar Graph

This bar graph shows the frequency of occurence of States/Provinces.

```
plt.figure(figsize=(10, 6))
sns.countplot(x='State (Province)', data=df)
plt.title('Bar Graph of States/Provinces')
plt.xlabel('State/Province')
plt.ylabel('Count')
plt.xticks(rotation=45)
plt.show()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/da3306a3-c012-4f0b-acbd-4366825e46c4)

**Figure 24: Bar Graph of States/Provinces**

</div>

From Figure 24, there are 2 states/provinces. Frequency of MS is higher than MT.

(C) Box Plot

This box plot shows how the Air Temperature is distributed in °C.
```
plt.figure(figsize=(8, 6))
sns.boxplot(y='Air temperature (instant) (°C)', data=df)
plt.title('Box Plot of Air Temperature')
plt.ylabel('Temperature (°C)')
plt.show()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/27ab7863-ebe4-4b77-988c-70787c1d54e4)

**Figure 25: Box Plot of Air Temperature**

</div>

We can determine median, quartile 1, quartile3 and outliers from Figure 25.

(D) Scatter Plot

This scatter plot shows the relationship between Air Temperature and Wind Speed.
```
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Air temperature (instant) (°C)', y='Wind speed (m/s)', data=df, alpha=0.5)

plt.title('Scatter Plot of Air Temperature vs. Wind Speed')
plt.xlabel('Air Temperature (°C)')
plt.ylabel('Wind speed (m/s)')

plt.show()
```

<div align="center">

![image](https://github.com/drshahizan/Python_EDA/assets/106257072/5efdd3bf-a2cc-4836-bf41-5163020f334c)

**Figure 26: Scatter Plot of Air Temperature vs. Wind Speed**

</div>

From Figure 26, the Air Temperature occurs more frequently above 20°C while Wind Speed occurs more frequently below 4.

(E) Pie Chart

This pie chart shows the percentages of Station Name of a whole.
```
column_for_pie = 'Station Name (usually city location or nickname)'

values = df[column_for_pie].value_counts()
labels = values.index

plt.figure(figsize=(8, 6))
plt.pie(values, labels=labels, autopct='%1.1f%%', startangle=90, colors=plt.cm.Paired.colors)
plt.title('Pie Chart of Station Name')

plt.show()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/3eccdb15-bb44-4968-a71c-bd150348516b)

**Figure 27: Pie Chart of Station Name**

</div>

From Figure 27, there are 2 station in this dataframe. Bela Vista has 80.7% while Nova Ubirata has 19.3%.

### Data Exploration

#### Correlation Heatmap
```
correlation_matrix = df.corr()
plt.figure(figsize=(12, 10))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f")
plt.title('Correlation Heatmap')
plt.show()
```
<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/e37419eb-de6a-46cf-85f4-ada4b17d6dd4)

**Figure 28: Correlation Heatmap**

</div>

• Atmospheric Pressure at Station Level(mB) has a negative correlation with Relative humidity with the value of -0.78.

• Atmospheric Pressure at Station Level(mB) also has a negative correlation with Dew Point Temperature with the value of -0.73.

• Dew Point Temperature has a positive correlation with Relative humidity with the value of 0.92.

#### Histograms of Numerical Variables
```
df.hist(bins=20, figsize=(30, 20))
plt.suptitle('Histograms of Numerical Variables')
plt.show()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/612e3bb5-c42a-492f-b6bb-2486549f3ecc)

**Figure 29: Histograms of Numerical Variables 1**

![image](https://github.com/drshahizan/Python_EDA/assets/106257072/91f20587-cc7a-4527-b601-164201bf44ec)

**Figure 30: Histograms of Numerical Variables 2**

</div>

```
sns.pairplot(df[['Dew point temperature (instant) (°C)', 'Relative humidity (% instant)', 'Atmospheric pressure at station level (mB)']])
plt.suptitle('Pair Plot of Dew point temperature (instant) (°C)', 'Relative humidity (% instant)', 'Atmospheric pressure at station level (mB)s')
plt.show()
```

<div align="center">
  
![image](https://github.com/drshahizan/Python_EDA/assets/106257072/e926169b-0b2d-492a-aeb4-6f6c6ffa7cb2)

**Figure 31: Pair Plot of Dew point temperature (instant) (°C), Relative humidity (% instant), Atmospheric pressure at station level (mB)**

</div>

### Feature Engineering

#### Binnning or Discretization

Convert continuous variables into categorical or ordinal variables by binning them into intervals. For instance, temperature ranges (e.g., cold, moderate, hot) or precipitation levels (e.g., low, moderate, high).
```
# Define temperature ranges
bins = [0, 10, 20, 30, 40]  # Define temperature ranges (e.g., cold, mild, warm, hot)
labels = ['Cold', 'Mild', 'Warm', 'Hot']  # Labels for the temperature ranges

# Create a new categorical column 'Temperature Category'
df['Temperature Category'] = pd.cut(df['Air temperature (instant) (°C)'], bins=bins, labels=labels)

```



## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
