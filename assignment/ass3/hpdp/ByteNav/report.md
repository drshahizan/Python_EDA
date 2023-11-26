<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 3: Exploratory Data Analysis (EDA) Using Big Data

### Group Name: BYTE NAVIGATORS
### Group Members:

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
| LOO ZHI YUAN            |A21EC0197      |ASSIGNMENT 3|
| SOO WAN YING              |A21EC0227      |ASSIGNMENT 5|
| LAU YEE CHI              |A21EC0042      |ASSIGNMENT 4|
| YEW RUI XIANG              |A21EC0149      |ASSIGNMENT 4|

### Table of Contents
+ [1. Introduction](#intro)
+ [2. Dataset Selection](#dataset_selection)
+ [3. Data Acquisition](#data_acquisition)
  + [3.1. Import Dataset](#import_data)
+ [4. Setting Up the Environment](#setup_environment)
  + [4.1. Install Necessary Tools & Libraries](#install_lib) 
+ [5. Data Preprocessing](#dataset_preprocessing)
+ [6. Exploratory Data Analysis](#eda)
  + [Pass and Fail Views](#passfail_dashboard)
  + [Total Number of Records](#total_dashboard)
  + [Pass Percentage](#pass_dashboard)
  + [Fail Percentage](#fail_dashboard)
  + [Maximum Value](#max_dashboard)
  + [Minimum Value](#min_dashboard)
  + [Average Value](#avg_dashboard)
  + [Number of Students and Grades](#numstu_grades_dashboard)
  + [Total Number of Grades](#grade_dashboard)
+ [7. Conclusion](#conclusion)
+ [Contributions](#contribution)

## 1. Introduction <a name = "intro"></a>

This report presents the findings of the Exploratory Data Analysis (EDA) conducted on a dataset focus on Jan 2020 from a medium cosmetics online store. The primary objectives of the EDA were to uncover insights into user behavior, identify patterns, and explore key trends within the dataset. By analyzing various aspects such as price distribution, correlation between variables, event types, and user engagement metrics, this EDA aimed to provide valuable information for strategic decision-making and optimization of the online store's performance.

## Objectives

1. **Understand Price Distribution:**
   - Explore the distribution of product prices to identify common price ranges and understand user preferences in terms of pricing.

2. **Evaluate Variable Correlation:**
   - Investigate the correlation between different variables (e.g., price, product_id, category_id, user_id) to discern any relationships or dependencies.

3. **Examine Event Type Distribution:**
   - Analyze the distribution of event types to gain insights into user interactions, with a focus on the frequency of views, cart additions, and purchases.

4. **Identify Top Categories and Products:**
   - Determine the most popular categories, products, and brands based on total purchase amounts, providing a glimpse into user preferences.

5. **Explore Daily, Hourly, and Weekly Trends:**
   - Investigate trends in user behavior on a daily, hourly, and weekly basis to understand peak activity periods, variations, and potential patterns.

6. **Analyze User Engagement Metrics:**
   - Examine metrics related to user engagement, including repurchased products, categories with high repurchase rates, and users with the highest purchase frequency.

7. **Visualize Weekly User Behavior:**
   - Utilize visualizations such as bar charts and funnel charts to portray and compare the number of different event types for each week.

8. **Gain Insights into Repurchased Products and User Engagement:**
   - Identify the top repurchased products, categories, and users with the highest engagement metrics, contributing to a deeper understanding of customer loyalty.

By achieving these objectives, the EDA aims to provide actionable insights that can inform strategic decisions related to inventory management, marketing strategies, and user experience enhancements.

## 2. Dataset Selection <a name = "dataset_selection"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/fb6f7aa1-9d05-4d4d-9c54-5fc71db911c6)
> Screenshot of the Main Page for Dataset in Kaggle

For assignment 3, we have choose a large dataset which is fullfil the requirement of more than 1 million data dataset from [Kaggle](https://www.kaggle.com/). We have choose a 501.79 MB ".csv" dataset which consist of 4264752 rows and 9 columns which are "event_time", "event_type", "product_id", "category_id", "category_code", "brand", "price", "user_id" and "user_session".

The title of the dataset is "**eCommerce Events History in Cosmetics Shop**" and we have choose the data of January 2020 which is "2020-Jan.csv" dataset.

Source of dataset:
https://www.kaggle.com/datasets/mkechinov/ecommerce-events-history-in-cosmetics-shop/data

| Property         | Description                                                                                                       |
|------------------|-------------------------------------------------------------------------------------------------------------------|
| event_time       | Time when event happened at (in UTC).                                                                            |
| event_type       | Only one kind of event: purchase.                                                                                 |
| product_id       | ID of a product.                                                                                                  |
| category_id      | Product's category ID.                                                                                            |
| category_code    | Product's category taxonomy (code name) if it was possible to make it. Usually present for meaningful categories and skipped for different kinds of accessories. |
| brand            | Downcased string of brand name. Can be missed.                                                                   |
| price            | Float price of a product. Present.                                                                               |
| user_id          | Permanent user ID.                                                                                               |
| user_session     | Temporary user's session ID. Same for each user's session. Is changed every time user comes back to the online store from a long pause.             |

## 3. Data Acquisition <a name = "data_acquisition"></a>

### 3.1. Import Dataset <a name = "import_data"></a>
![image](https://github.com/drshahizan/Python_EDA/assets/95710157/d1feeab9-5e19-427b-8dfd-1c436c77a2d9)

Mount the google colab to my personal google drive.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/74c88a9a-6d00-478c-91ce-04e1c0b01f0b)

Importing the dataset which is "2020-Jan.csv" in zip file format.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/f80f4604-eef3-47e5-827c-36a5dec581b4)

Read the first 5 rows of the dataset to ensure the dataset imported successfully.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/24a9a29b-8b1f-4ed3-a405-b192a5fa2534)
> Ouput of the "df.head()"

## 4. Setting Up the Environment <a name = "setup_environment"></a>

### 4.1. Install Necessary Tools & Libraries <a name = "install_lib"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/a4a3101f-9e06-443d-9a3e-71798ea9655c)
> Imported Tools and Libraries

| Library/Tool               | Description                                                                                                   |
|------------------------|---------------------------------------------------------------------------------------------------------------|
| pandas                 | Data manipulation and analysis library.                                                                      |
| numpy                  | Numerical operations library.                                                                                 |
| matplotlib.pyplot      | Plotting library for creating static, animated, and interactive visualizations.                               |
| seaborn                | Data visualization library based on Matplotlib that provides a high-level interface for drawing statistical graphics.|
| plotly.express         | Plotly's high-level interface for creating interactive plots.                                                |
| plotly.graph_objects   | Low-level interface for creating complex, customized plots with Plotly.                                       |
| plotly.subplots        | Module for creating subplots with Plotly.                                                                    |
| dask.dataframe         | Dask library for parallel computing with larger-than-memory datasets.                                        |
| os                     | Operating system interface for interacting with the file system.                                              |
| missingno              | Library for visualizing missing data in a dataset.                                                           |
| datetime               | Module for working with dates and times.                                                                      |

## 5. Data Preprocessing <a name = "dataset_preprocessing"></a>

### 5.1. Data Exploration <a name = "data_explore"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/01687796-07cd-42ea-875c-95af15aaba18)

Read and display the first 5 rows of the dataset.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/3d69f4f5-7ff1-41aa-80da-e75a19a3c0d2)

Read and display the last 5 rows of the dataset.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/c5955189-ae6b-4093-b37b-56de44f7b55c)

Display the shape of the dataset in (row, column) format.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/6f4fd88b-790c-4f02-bcc5-d98c5698a624)

Read and display the information of the dataset.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/ee9e9165-14d4-4c5d-94b9-745eb2d8bfe5)

Provides a quick overview of the distribution and central tendency of the selected float64 columns in the dataset.

### 5.2. Data Cleaning and Handling <a name = "data_clean"></a>

#### 5.2.1. Handle Missing Values <a name = "missing_value"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/831fa7da-a563-4988-8e9c-533b3b277987)

Determine the sum of null values for each columns.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/23b924b0-b7f0-45cf-bf73-51d990a851a5)

Plot and visualise the bar chart of missing values.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/0d737951-6ebb-4709-828d-e237736cf6d1)

Plot and visualise the dendrogram of missing values.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/c604aac7-40f9-4577-b0e7-e62ce602099e)

Plot and visualise the matrix of missing values.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/5a40190f-d623-4bc2-b5f4-663db3e521d0)

Calculate the percentage of null values for each columns droping columns consisting null values greater than 90%.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/40372e65-3d9b-4adf-8244-616c61af23de)

Drop the columns consisting null values greater than 90% which is the column category_code is dropped.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/d93ba2a2-8b46-4eff-9203-851472100225)

Cheking the latest columns of the dataset to ensure column category_code is dropped successfully.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/e70b6d07-4fb6-45b0-90d2-30e1d6a04731)

Replace the missing vaules in 'brand' column with 'unknown' and replace the missing vaules in 'user_session' column with mode value.

#### 5.2.2. Handle Duplicated <a name = "handle_dup"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/349d7f4b-9f89-40a3-8e1f-754fa9927cf6)

Determine the sum of duplicated rows or values for the dataset and then calculate the percentage of duplicated rows for the dataset.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/f69e228e-2000-497c-a223-cc80f341238b)

Plot and visualise the duplicated values by using histogram.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/878626e5-0abc-463e-8cb2-c7aca41a6503)

Drop or remove the duplicated rows in the dataset and modify it in place.

#### 5.2.3. Handle Datatypes <a name = "handle_dt"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/3d7ace76-b6e4-4956-be08-918589c0e789)

Checking for the datatype for columns by using df.info().

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/e38e7733-50f1-4062-a7a9-6302613509f1)

Checking the details for the column event_time.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/a3359002-d625-45f7-a692-5c147657f07d)

Removing ' UTC' string from each value in the 'event_time' column. Then, converting the 'event_time' column to datetime64 data type and converting the 'event_type' column to categorical data type.

Lastly, check the information of datatypes for each column using df.info() again.

#### 5.2.4. Column 'price' <a name = "price"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/e828afd1-bbd4-401f-b28d-75233e66ce5c)

Checking whether the price consisting negative values and handle it by droping those rows.

## 6. Exploratory Data Analysis <a name = "eda"></a>

## 7. Conclusion <a name = "conclusion"></a>

### Insights Gained and Key Findings through the EDA Process:

### 1. Price Distribution:

- The histogram analysis of prices indicates that the majority of products fall within the price range of 0 to approximately 10, with a decreasing frequency as prices increase. Common price ranges within the dataset are observed to be from 0 to 50.

### 2. Correlation Analysis:

- Correlation matrix heatmap reveals weak associations between 'price' and other variables ('product_id', 'category_id', 'user_id'). Notably, 'price' and 'category_id' show no linear correlation, suggesting independence.

### 3. Event Type Distribution:

- The histogram of event types illustrates that 'view' is the most frequent event type, constituting 50.4% of all events, followed by 'cart' with 28.0%. This suggests that a significant portion of user interactions involves product viewing.

### 4. Top Categories and Products:

- Categories '1487580005092295511' and product '5560754' emerge as the most popular based on the bar plots. Additionally, the brand 'runail' dominates in terms of orders or total purchase price.

### 5. Daily Trends:

- Daily trends showcase a positive correlation between total purchase amounts and the count of purchase events. Specific dates, such as 26, 27, and 28, exhibit higher order counts, indicating potential seasonality or promotional events.

### 6. Hourly and Weekly Trends:

- Hourly trends reveal consistent purchasing behavior between 8 to 19 hours. Order count spikes as the weekend approaches and is highest on Tuesday, indicating variations in user activity based on the day of the week.

### 7. Weekly User Behavior:

- The bar chart and funnel chart visualize weekly user behavior, emphasizing the count and progression of different event types. These charts provide insights into user engagement and conversion rates throughout the weeks.

### 8. Top Repurchased Products and User Engagement:

- Specific products, such as #5809910, emerge as highly repurchased, emphasizing their sustained popularity. User #469299888 stands out with the highest weekly purchase frequency and the most number of purchased items, indicating a loyal and engaged customer.

### 9. Categories with High Average Repurchased Count:

- Certain categories exhibit a consistently high average repurchased count, indicating sustained popularity and customer loyalty.

In conclusion, the EDA process has provided a comprehensive understanding of user interactions, product preferences, and purchasing patterns. These insights can inform strategic decisions related to inventory management, marketing strategies, and user engagement initiatives to enhance the overall performance of the online store.

## Contribution 🛠️  <a name = "contribution"> </a>
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
