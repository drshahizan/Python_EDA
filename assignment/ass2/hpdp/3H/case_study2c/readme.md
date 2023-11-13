## In this case study Pandas-Profiling is used as the Automated EDA for exploratory Analysis

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/assets/142320760/960b4990-9c9c-4b3b-af8f-00cb37388fd8" alt="Your Image">
</p>


Pandas Profiling is a Python library that provides an easy and efficient way to perform exploratory data analysis (EDA) on a dataset using the popular pandas library. It generates a comprehensive HTML report with various insights and visualizations that help you understand the structure, distribution, and relationships within your dataset.

In case study 2c, we will see the capability of pandas profiling in handling Malaysian dataset. 
To see the full dashboard result you can download the output.html file and open through your device.

# Case Study 2C: Exploratory Data Analysis using Automated EDA Tools (Pandas Profiling)

## Step 1: Selecting Automated EDA Tool

Pandas Profiling is a powerful tool used in data analysis with Python that generates a comprehensive report summarizing the characteristics of a dataset. It's an exploratory analysis tool that automates the process of gaining insights and understanding the structure and content of a DataFrame. Here's a brief explanation of Pandas Profiling:

```
pip install ydata-profiling
```

## Step 2: Select a Malaysia dataset
The dataset can be downloaded from https://drive.google.com/file/d/1-6jBhXqAKTa3_2SUxo5lnhLcaMYD4Wkv/view
The dataset is also uploaded to Github. In this project, we will link the dataset from Github.

### Overview Of The Dataset
The data are collected from an app called PriceCatcher which is a mobile app developed by the Ministry of Domestic Trade and Cost of Living (KPDN, formerly KPDNHEP) to help users compare the prices of key items in their area. Prices are collected and verified by groundstaff on a daily basis, with over 2 million prices collected every month. The dataset that we used are recorded from the year 2022/01 - 2023/10.

## Step 3: Perform data preparation & cleaning

- Load the dataset into a data frame using Pandas
- Explore the number of rows & columns, ranges of values etc.
- Handle missing, incorrect and invalid data
- Perform any additional steps (parsing dates, creating additional columns, merging multiple dataset etc.)

__Dataset Attribute with Description__ <br>

The dataset has 21798112 rows and 12 columns

|Attribute|Description|
|:--------|:----------|
|`Index`|Number or rows|
|`date`|Date of the price of item recorded|
|`price`|Price of item|
|`item`|Item name|
|`unit`|Quantity of item|
|`item_group`|Item group |
|`item_category`|Item Category|
|`premise`|Premise Location|
|`address`|Premise Full Address|
|`premise_type`|Type of premise|
|`state`|State Location|
|`district`|District Location|

__Importing Dataset Using Pandas__ <br>
The dataset are in .zip as we combine some of the dataset into one including the flag and etc. For your information the data are cleaned which resulting in no null and empty values.

```
import numpy as np
import pandas as pd
from ydata_profiling import ProfileReport
```

```
from google.colab import drive
drive.mount ('/content/drive')
```

```
import zipfile
```

```
zip_file_path = '/content/drive/MyDrive/Colab Notebooks/DATASET/data.zip'
```
```
extraction_path = '/content/drive/MyDrive/Colab Notebooks/DATASET'
```
```
with zipfile.ZipFile(zip_file_path,'r') as zip_ref:
  zip_ref.extractall(extraction_path)
```
```
df = pd.read_csv('/content/drive/MyDrive/Colab Notebooks/DATASET/data.zip', compression = 'zip', index_col = 0)
```
```
df.head()
```

![Screenshot 2023-11-13 101925](https://github.com/drshahizan/Python_EDA/assets/142320760/bf7f2c1c-711a-40ae-87cf-04efa6a62e6c)


__Number of row, column and range__
```
df.info()
```

![Screenshot 2023-11-13 101931](https://github.com/drshahizan/Python_EDA/assets/142320760/b5eff6ba-dbc6-4098-ba13-13530eeeb5fc)

```
df.isnull().sum(axis=0)
```
![Screenshot 2023-11-13 101935](https://github.com/drshahizan/Python_EDA/assets/142320760/a7f75666-a8a7-414e-be15-dfdb18c1ca31)

__Drop Unwanted Column__
```
#df.drop('item',axis='columns', inplace=True)
df.drop('address',axis='columns', inplace=True)
df.drop('premise',axis='columns', inplace=True)
df.head()
```
![Screenshot 2023-11-13 101942](https://github.com/drshahizan/Python_EDA/assets/142320760/b5e0bd77-8916-4e1e-b239-d1ba648e27a1)
```
distinct_state = df['state'].unique()

print(distinct_state)
```

![Screenshot 2023-11-13 101947](https://github.com/drshahizan/Python_EDA/assets/142320760/120c3ca3-30fe-45c9-9b42-a1538a8b4d43)

```
filtered_df = df[df['state'] == 'Negeri Sembilan']
filtered_df
```
![Screenshot 2023-11-13 101952](https://github.com/drshahizan/Python_EDA/assets/142320760/1e2aabbc-2cd3-4145-8bb9-3b3cda2ec0ec)

## Step 4: Implementation Of Automated EDA Tools
__a. Loading dataset into the tool__ <br><br>
This code snippet utilizes the pandas_profiling library in Python to generate a comprehensive profiling report for a pandas DataFrame, denoted as df. The ProfileReport class is employed, taking the DataFrame as input and allowing for the optional specification of a title, set here as "Profiling Report." The resulting profile object encapsulates the analysis, which can be further utilized to produce the profiling report. This report encompasses a range of insights, including data types, missing values, and summary statistics, providing a quick and thorough overview of the dataset's characteristics. Finally, depending on the version, the report can be saved to an HTML file using the to_file method or displayed interactively using to_widgets.


```
profile = ProfileReport(filtered_df, title="Profiling Report", html={'style':{'full_width':True}})
```
__b. Generate Basic Statistic & Visualization__ <br><br>
Pandas Profiling is a handy tool for Exploratory Data Analysis (EDA). When you run ProfileReport on your DataFrame, it generates a comprehensive report with various insights.

<br>

Basic Statistics:

+ Essentials: It gives you a quick overview of your dataset, including the number of variables, missing values, and unique values.

+ Quantiles and Descriptive Stats: You get a sense of the distribution of your numerical data with minimum, maximum, mean, and other descriptive statistics.

<br>

Correlation:

+ Correlation Matrix: A heatmap showing the correlation between numerical variables. This helps identify potential relationships between features.

<br>

Visualizations:

+ Histograms: Visual representation of the distribution of numerical data. Helps spot patterns and outliers.

+ Scatter Matrix: Pairs of numerical features are plotted against each other. Useful for identifying relationships or clusters.

+ Categorical Plots: For categorical variables, it provides bar charts to show the distribution of categories.

<br>

Missing Values:

+ Matrix Plot: A visual representation of missing values. Helps to identify patterns and extent of missing data.
Unique Values:

+ Table of Unique Values: For each column, it lists the unique values and their frequency. Useful for categorical variables.
And More:

<br>

Warnings:
+ Flags potential issues in your data, like high cardinality or constant features.

```
#To see Pandas Profiling Dashboard open google colab and run this code, make sure to run from the beginning as we need to install and import Pandas Profiling
profile
```

![Screenshot 2023-11-13 102818](https://github.com/drshahizan/Python_EDA/assets/142320760/e71a35fc-dbb4-4ece-a12e-af2a667c1246)

```
#To download the dashboard run this code
profile.to_file(output_file = "output.html")
```

__c. Exploring relationships and patterns in the data__ <br><br>

![Screenshot 2023-11-13 103112](https://github.com/drshahizan/Python_EDA/assets/142320760/28754738-e352-472e-8b28-52478a0021d1)
![Screenshot 2023-11-13 103208](https://github.com/drshahizan/Python_EDA/assets/142320760/a4f4b087-5aec-414d-a26f-79d85f003a3b)

After Pandas Profilling dashboard appear, we can easily see the overview page that displays the dataset statistics and the datatype that presents.

<br>

For further exploring the dataset's patterns and correlation, we can scroll down the interface and see a heat map which indicates the correlation between variables and this insights can be used as a variable when producing a visualization. In this case, item_category has the highest correlation with the item_group.

__d. Unique Featues & Capabilities Of Pandas Profiling__ <br> <br>

Comprehensive Overview: Pandas Profiling generates a detailed and comprehensive
overview of your dataset, including basic statistics, distribution of values, and data types. This can save a significant amount of time compared to manually inspecting the data.

<br>

Missing Values Analysis: The profiling report includes an analysis of missing values, providing insights into the percentage and distribution of missing data in each column. This is crucial for understanding data quality.

<br>

Variable Interactions: The report identifies potential interactions or correlations between variables, helping you understand how different features in your dataset relate to each other.

<br>

Sample Data: The report includes a sample of the actual data, allowing you to inspect specific rows and get a sense of the dataset's content.

<br>

Export Options: You can export the profiling report to different formats, such as HTML or widgets, making it easy to share and integrate into your workflow.

<br>

Configurability: Pandas Profiling offers a range of configuration options, allowing you to customize the analysis based on your specific needs. You can choose what elements to include or exclude in the report.

## Step 5: Pros And Cons Of Pandas Profiling

Pros: <br>


*   Time-Saving: Pandas Profiling automates the process of data exploration, saving a significant amount of time compared to manual inspection and analysis.

*   Comprehensive Overview: It provides a comprehensive overview of the dataset, including basic statistics, distribution plots, and correlation matrices, helping users quickly understand the characteristics of the data.

*   Missing Values Analysis: The tool offers a detailed analysis of missing values, aiding in identifying and addressing data quality issues.

Cons: <br>
*   Resource Intensive: For large datasets, generating the profiling report can be resource-intensive and may take a significant amount of time and memory.

*   Limited Customization (Depending on version): While there is some configurability, more advanced users may find the level of customization limiting for specific analysis needs.

Insights: <br>
*   Based on my experience using Pandas Profiling, it is an amazing EDA tool which helps us in basic visualization as it gives us indepth insights. But the downside of it is that if the dataset is too large it will consume a lot of time to run that maybe lead to error in compilation. That is why in my analysis I decided to narrow down my scope of analysis to one state which is "Negeri Sembilan" so that it can be run smoothlt.


## Step 6: Conclusion <br>

Insights Gained From Analysis: <br>


*   Veggies are the most common item sold in Negeri Sembilan that recorded with a frequency of over 25%
*   Hygiene products recorded the least in the item_group category which means that the target item that a seller wants to sell are mostly groceries as it has the highest item sold.
*   In Negeri Sembilan, there are over 400 thousand supermarket which resulting that residents in the states can get their neccessities easily.

<br><br>

Recommendation:<br> <br>
Pandas Profiling is notably well-suited for datasets predominantly composed of numerical variables, showcasing its strength in delivering detailed insights into quantitative aspects of the data. The tool's proficiency lies in generating comprehensive statistical summaries, distribution plots, and correlation matrices, providing a deep understanding of the numerical characteristics within the dataset. While it certainly offers valuable insights for categorical data as well, Pandas Profiling's emphasis on numerical analysis makes it particularly beneficial for users seeking to unravel patterns, relationships, and statistical nuances within a primarily numerical dataset. Therefore, using a dataset that is mostly categorical like this dataset is not recommendable.

## Step 7: References <br>

https://pypi.org/project/pandas-profiling/ <br>
https://github.com/ydataai/ydata-profiling <br>
https://www.youtube.com/watch?v=Ef169VELt5o




