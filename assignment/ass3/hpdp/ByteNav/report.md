![image](https://github.com/drshahizan/Python_EDA/assets/95710157/323890af-4219-4615-8de7-2a56e1e69b02)![image](https://github.com/drshahizan/Python_EDA/assets/95710157/c1a0ae1c-0561-4d52-bcc2-f8003ea7d33e)<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
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
  + [5.1. Data Exploration](#data_explore)
  + [5.2. Data Cleaning and Handling](#data_clean)
    + [5.2.1. Handle Missing Values](#missing_value)
    + [5.2.2. Handle Duplicated](#handle_dup)
    + [5.2.3. Handle Datatypes](#handle_dt)
    + [5.2.4. Column 'price'](#price)
+ [6. Exploratory Data Analysis](#eda)
  + [6.1. Summary Statistics](#sum_stat)
  + [6.2. Data Visualization](#data_visual)
  + [6.3. Data Exploration](#data_explore_eda)
  + [6.4. Feature Engineering](#fe)
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

### 6.1. Summary Statistics <a name = "sum_stat"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/9cf97740-683a-4df2-ad65-83a808f4d151)

Generate descriptive statistics of a dataset and provides a quick overview of the distribution and central tendency of all numerical columns in dataset.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/1224e268-aaa6-47c4-957e-67d2cd673920)

Get the total number of user engagement in each event type.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/f62c9c4a-a5da-42c8-9c47-0a0471504eeb)

Get the summary for spending of users on purchasing product in Cosmetics Shop eCommerce websites.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/36bcc9f7-308b-4351-a698-98445570e376)

Display the summary of the distribution and central tendency of the 'spent' values in the price_df_ dataframe created above.

### 6.2. Data Visualization <a name = "data_visual"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/d3f2d060-6277-4f39-8c06-0bb8392bbde9)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/44932d09-254b-4953-a158-847152641d5c)

Based on histogram above, we have visualise the distribution of price which divide into certain ranges. As we can observe, the price range from 0 to approximately 10 have the highest frequency. In addition, we can see that, the frequency is getting lower when the price is increasing. In sum, we can sum up that the common prices ranges within the dataset are from 0 to 50.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/bb4ebdc7-6e7c-4854-9058-ba38c87a8dcd)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/5e39e39a-9e1e-4e4f-ab2e-787d429849a9)

Based on boxplot above, we have visualise the distribution of price for each of the different event types. It is represent by the interquartile range (IQR) of prices.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/6e63917e-e953-4db8-ac8b-ffe58ae06aac)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/860d7e56-98d9-4f34-a1aa-c23cf8f780e5)

**Insights Gained:**

- 'price' and 'product_id' have a very weak negative correlation (-0.02), suggesting a minimal association.
- 'price' and 'category_id' show no linear correlation (0.00), indicating independence.
- 'price' and 'user_id' exhibit a very weak positive correlation (0.03), suggesting a minimal association.
- 'product_id' and 'user_id' have a very weak negative correlation (-0.02), indicating a minimal association.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/e9751bf7-7925-46ad-a063-43ba3205fff3)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/96da65f9-a56b-46dd-bb56-927f9ea085d4)

Based on the histogram above, we have visualise the distribution of event type. As we can see that 'view' having the most which is 50.4% and following by cart which is 28.0%.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/ca948f0d-2fa6-432e-bb3e-6053f00ba0ae)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/0d448758-70f3-407d-8084-0c56128667e3)

The visualisation above shown the category with most orders. As we can observe from the bar plot, the category '1487580005092295511' have the most orders or total purchase price.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/7c0a2ec2-94d8-44b7-b4d9-e09dac265d43)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/7ebafbc6-2679-487f-8585-92e8786e737e)

The visualisation above shown the product with most orders. As we can observe from the bar plot, the product '5560754' have the most orders or total purchase price.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/63ced3e0-d081-4c07-bc3d-eacabc1037e0)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/d556c768-9774-42e7-9a92-fff5d4c7a706)

The visualisation above shown the brand with most orders. As we can observe from the bar plot, the brand 'runail' have the most orders or total purchase price. We also can see that there is a lot of unknown.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/de558fd5-7a53-42d0-b4dd-3999977bb767)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/127206c7-2e81-4d7f-a123-53308ce6ad3d)

The graph above visualises the daily trends of purchase orders over time. The blue line represents the total purchase price for each day, while the red line shows the count of purchase events on the same plot. The y-axis on the left corresponds to the total purchase price, and the y-axis on the right corresponds to the count of purchase events.

**Insights Gained:**

- The plot allows us to observe the relationship between the total purchase amount and the number of purchase events on a daily basis.
- The blue line provides insights into the overall spending trends, showing days with higher or lower total purchase amounts.
- The red line indicates the daily variation in the number of purchase events, helping to identify days with increased or decreased purchasing activity.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/d2e26972-fab5-41f7-aebc-ce84d8fd12e1)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/70fcae69-3ee6-4372-9c94-0df338f28a98)

The graph visualises the trends of purchase orders by the hour of the day, breaking down the data into hourly intervals. It includes both the total purchase price (blue line) and the count of purchase events (red line) on the same plot. The x-axis represents the hours of the day.

**Insights Gained:**

- The blue line shows the variation in total purchase amounts throughout the day, highlighting peak and off-peak hours.
- The red line represents the count of purchase events each hour, indicating the hourly distribution of purchase activities.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/808b5629-2dab-4d26-a8d5-b03087ebb51b)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/d3de48b9-ce64-4427-b41d-5f45b35e2547)

The graph visualises the trends of purchase orders by the day of the week, breaking down the data into daily intervals. It includes both the total purchase price (blue line) and the count of purchase events (red line) on the same plot. The x-axis represents the days of the week, starting from Monday (0) to Sunday (6).

**Insights Gained:**

- The blue line shows the variation in total purchase amounts throughout the week, highlighting days with higher or lower spending.
- The red line represents the count of purchase events each day, indicating peak activity days.
- The plot provides insights into the weekly patterns of purchase behavior, helping to identify the most active days and potential correlations between total spending and event count.


**Insights Gained:**

- The trends of total purchase amounts and the count of purchase events by date indicate a positive correlation. As total spending increases, the number of purchase events also tends to rise.
- Specific dates, such as 26, 27, and 28, stand out with higher order counts. Further analysis can explore if there is seasonality or specific promotions on these dates.
- The trends of orders by hour showcase consistency in both total purchase amounts and the count of events between 8 to 19 hours. There is a stable purchasing behavior during standard business hours.
- Order count spikes as we get close to weekday and is highest on Tuesday. This indicates that users tend to make more purchases towards the start of the week.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/76534f32-6b08-4f75-b421-d631dc1d6ead)

Based on the bar chart above, we have visualise the event_type, event_week and event_count to show and compare the number of different event type for each week.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/55ad3c6d-69a2-48f9-8605-c968dd0911b4)

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/dc3a0305-8bf9-4de1-a89d-fd878be88ee6)

Based on the funnel chart above, we have visualise the weekly user behavior based on the event type of view, cart and purchase.

### 6.3. Data Exploration <a name = "data_explore_eda"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/62101f6a-d7bc-43bb-bb31-e345a3f7cf32)

The code above use to explore the top 5 repurchased products.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/0ad471f5-51aa-42c6-a8fe-8aa300952b3f)

The code above use to explore the products with largest average repurchased count.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/6fdb39ff-e6b2-43be-a647-6e558d629f3c)

The code above use to explore the top 5 categories with the largest average repurchased count.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/0944b52a-3731-4253-a8eb-cd88d881c7ec)

The code above use to explore the most purchased product by different user.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/9d7454af-59ef-4b51-a0e7-88603842f45b)

The code above use to explore the user with the highest purchase frequency.

![image](https://github.com/drshahizan/Python_EDA/assets/95710157/bdefda36-8ec5-4f95-9289-bdc241a2df88)

The code above use to explore the user who purchased the most number of items.


**Insights Gained:**

Top 5 Repurchased Products:

- Product #5809910 from category ID 1602943681873052386 is the most repurchased product with a count of 2029 purchases.
- The top 5 repurchased products are dominated by product #5809910, indicating a high level of popularity and demand for this item.

Products with the Largest Average Repurchased Count:
- Products with IDs 5854171, 5854180, and 5850311 have the largest average repurchased count, each with an average of 4.0.
- This suggests that these products are not only frequently repurchased but also maintain a consistent level of demand over time.

Top 5 Categories with the Largest Average Repurchased Count:

- Categories with category IDs 1924049106385240809, 1487580007675986893, and 1487580005134238553 have the largest average repurchased count, indicating sustained popularity in these categories.

Most Purchased Product:

- The most purchased product is #5809910, bought by 1932 different users. This highlights a widespread appeal and adoption of this specific product.

User with the Highest Weekly Purchase Frequency:

- User #469299888 has the highest purchase frequency on a weekly basis, making 262 purchases. This user demonstrates a consistently high engagement level with the online store.

User with the Most Number of Purchased Items:

- User #469299888 has also purchased the most number of items, totaling 262. This user stands out as a significant contributor to the overall purchase count.

### 6.4. Feature Engineering <a name = "fe"></a>

The feature engineering is not applicable as there is no need to create new features or transform existing ones to support our analysis.

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
