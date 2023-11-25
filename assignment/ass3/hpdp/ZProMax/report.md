<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 3: Exploratory Data Analysis (EDA) Using Big Data

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/e60d2615-598d-4d7b-bc9c-3a178d0f0ffc)

### Group Name: ZProMax
### Group Members:

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
| LING WAN YIN           |A21EC0047     |ASSIGNMENT 3|
| NG SUANG JOO             |A21EC0102      |ASSIGNMENT 4|
| FONG KHAH KHEH            |A21EC0026      |ASSIGNMENT 5|

### Table of Contents:
+ [1. Dataset Selection](#dataset_selection)
+ [2. Data Acquisition](#data_acquisition)
+ [3. Setting Up the Environment](#setup_environment)
   + [Import necessary libararies and tools](#imports)
   + [Helpful functions and classes](#func)
   + [Reading data](#read_data)
+ [4. Data Preprocessing](#dataset_preprocessing)
   + [Handling missing value](#missing_value)
   + [Data standardization](#data_standard)
   + [Dropping unnecessary columns](#drop_column)
+ [5. Exploratory Data Analysis](#eda)
   + [Summary Statistics](#summary)
   + [Data Visualization & Data Exploration](#data_vis)
      + [Univariate Analysis](#uni_var)
      + [Correlation](#corr)
      + [Feature Engineering](#fe)
      + [Bivariate Analysis](#bi_var)
+ [6. Conclusion](#conclusion)
+ [Contributions](#contribution)

## 1. Dataset Selection <a name = "dataset_selection"></a>
The dataset `'searches.csv'` reflects every search query entered on the bus rides booking platform in New York. This dataset is sourced from the [Kaggle](https://www.kaggle.com/datasets/asimzahid/new-york-bus-rides-service?select=searches.csv) website. 

**Dataset descriptions:**
- This dataset has a total of 5699336 records with 13 columns of attributes.

The following shows the **attributes** and its **representations**.  
|Attribute|Description|
|:--------|:----------|
|`session_id`|Session of the search|
|`search_id`|Unique search in the session|
|`user_id`|ID of the user|
|`search_city`|City where the search happened|
|`search_time`|Local time of the search|
|`num_of_results`|Number of results returned for the search |
|`is_result`|Whether a search gave a result or not|
|`median_pickup_walk_time`| Estimated time taken by user to walk from his desired pickup to the bus station|
|`median_dropoff_walk_time`|Estimated time taken by user to walk from the bus station his desired destination|
|`median_bus_travel_time`|Estimated bus travel time|
|`high_demand_val`|Indicates very few seats left or that the bus is full|
|`user_device_os`|Platform of the mobile device|
|`user_device_app_version`|App version number|

## 2. Data Acquisition <a name = "data_acquisition"></a>
The dataset `'searches.csv'` is retrieved from the Kaggle website in the form of a **CSV (Comma-Separated Values)** file, a widely used format for tabular data that integrates seamlessly with various big data processing tools. Obtaining a dataset in a format that matches the compatibility of big data tools is important to ensure effective processing and analysis.

## 3. Setting Up the Environment <a name = "setup_environment"></a>
**a) Import necessary libraries and tools** <a name = "imports"></a>

In this assignment, we make effective use of multiple Python libraries to analyze and visualize data. We use **Dask** for parallel processing, which allows us to handle datasets larger than memory and compute more quickly, **Numpy** and **Pandas** for basic data manipulation, and **Matplotlib** in conjunction with **Seaborn** to produce informative visualizations that help us understand and convey our findings.

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/af34cfed-c801-44c3-9e6f-a04f14cc95ab)

**b) Helpful functions and classes** <a name = "func"></a>

The following are the helpful functions and classes used in performing this EDA:

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/b4972d7b-b736-48bd-ad60-0c8150264b4f)
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/40491dc7-ce6e-4ddc-8a15-f4e9b296207b)

**c) Reading data** <a name = "read_data"></a>

1. Mount the Google Drive to access the file as we locate the `'searches.csv'` in the Google Drive.
   
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/6da34ee0-663a-4d67-b997-a8c8da7fb8a0)

2. Use **Dask** to read the `'searches.csv'` file from the specified path in Google Drive. The **'*assume_missing=True*'** parameter helps handle missing values efficiently. Then, compute the **Dask DataFrame** to obtain a **Pandas DataFrame** as Dask functions inactively until it is explicitly computed.
   
  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/2a96d16d-02d6-4d07-a220-fe6f55cc4239)

3. Display some of the data to ensure that we have loaded the correct data into the Google Colab.
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/6b444c1a-db23-4e2b-9ea1-2b91f444e6f8)

## 4. Data Preprocessing <a name = "dataset_preprocessing"></a>
Data preprocessing is performed to prepare the data for the Exploratory Data Analysis (EDA). 
Before performing the data preprocessing tasks, it is crucial to get an overview of the data to better understand the data. To do this, the following are the codes that have been executed in [Google Colab](ass3.ipynb). 

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/75537867-bc7c-478d-b05c-f4d4dbd221a7)

Then, proceed to the data preprocessing tasks. The following are the **data preprocessing tasks** that have been carried out:
#### a) Handling missing value <a name = "missing_value"></a>

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/21f97ac6-8344-43c9-ae0b-8f8337c6bd8c)

It is observed that there are missing values in the columns `median_pickup_walk_time`, `median_dropoff_walk_time` & `median_bus_travel_time` and this could possibly be due to the `is_result` being **'False'**. `is_result` being **'False'** means that the search for bus rides is unsuccessful. Thus, in this case, impute missing values with the value of zero.

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/3a03e566-21f4-457d-bcfe-c824a4c57a4a)

Whereas, handle the rows of `median_pickup_walk_time`, `median_dropoff_walk_time`& `median_bus_travel_time` having **'True'** (`is_result`) by imputing with the median value.

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/879dfdaa-43e8-4c1f-820c-786c686e529a)

The missing values in the column of `user_device_os`and `user_device_app_version` are associated with each other. Imputing it with the most frequent value of each column will be reasonable. 

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/6acea83e-965e-48e3-b2dc-deda42fc5292)

After that, generate an overview of the data to determine whether there exists missing value. The data overview is shown as below.

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/ef3a876a-923c-4008-b447-89e413a8dfca)

#### b) Data standardization <a name = "data_standard"></a>
From the table above, the results (unique_value_count) of the `user_device_os` is weird, it should be the value of 2 instead. So, from the investigations carried in the [Google Colab](),
it is obeserved that values are **'android'**, **'ios'**, **'iOS'**. 

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/3f4bb318-44d9-4a90-9db0-39fb34ad219f)

Generally, the word '**ios**' has the same meaning as '**iOS**'. So, in this case, replace the word '**iOS**' with '**ios**'. So, perform the data standardization to standardize the value such that it will provide an accurate result in EDA later. 

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/a1cb5a27-ff8e-475f-ac48-6ef3f4e80b29)


#### c) Dropping unnecessary columns<a name = "drop_column"></a>
The percentage of uniqueness of the column `search_city` is **0%**, which means every row has the same value. So, drop the column as it does not provide any distinguishing features. The same goes for the duplicate rows.

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/dd23b5b7-c86e-47da-b80d-d1c3742cbca5)

Since the uniqueness percentage of `user_id` is significantly low **(3.54%)**, check whether there are any duplicate values.

![image](https://github.com/drshahizan/Python_EDA/assets/146581747/172deebb-35e9-4abe-bdb6-39c0fdadf46a)

After all the data preprocessing tasks, the data should be ready for analysis.

## 5. Exploratory Data Analysis <a name = "eda"></a>
### Summary Statistics <a name = "summary"></a>
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/0a2801bc-f7b8-4fd4-a3ec-f06cb3db6ee6)
> The table above displays an overall summary of the statistics of the numeric attributes in the dataset.
> 
### Data Visualization & Data Exploration  <a name = "data_vis"></a>

##### Univariate analysis  <a name = "uni_var"></a>
  - user_id
    <br>
    ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/d10d5dba-aa3a-4012-8c25-8b4c2e5769f5)

   > We have found that some `session_id` and `search_id` are being used by duplicated `user_id`, even though pandas.DataFrame.duplicated has not detected any. It is because one `user_id` may search for bus rides numerous times on different days or times.
<br><br>

 - search_time
    <br>
    ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/c79a6286-afbf-442c-b2e3-9568e2880c98)
    
   > The distribution of  `search_time` is dispersed.
    
 -  num_of_results
    <br>
   ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/90a4d664-1e2d-44cc-8c91-f290478a54ea)

   > The box plot represents the number of results from searching for bus rides in New York. From the box plot, we can tell that the `num_of_results` is positively skewed with a concentration of values around the lower end.
<br><br>

  - is result

  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/7c8b4e98-de61-4cce-bc33-a5ec74152a22)

  > There are more successful searches than unsuccessful searches, which means the chances of users searching for a bus ride remain optimistic.
 <br><br>
    
  -  median_pickup_walk_time
   ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/7a1e302a-4e9f-4015-87fb-b90a8442af62)

   > There are counts of `median_pickup_walk_time` value of **0** because the process of replacing the **null** value with **0** for `is_result = 'False'` during data preprocessing as having `'False'` denotes the failure of the searching process for bus rides.
<br>


 -  median_dropoff_walk_time
   ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/14065219-d9d1-4a1b-a6c4-f4c23d206aa7)

   > There are counts of `median_dropoff_walk_time` value of **0** because the process of replacing the **null** value with **0** for `is_result = 'False'` during data preprocessing as having `'False'` denotes the failure of the searching process for bus rides.
<br>

  
  -  median_bus_travel_time
  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/52117ce6-e82b-4f7c-81b1-469f02fc305c)

 > There are counts of `median_bus_travel_time` value of **0** because the process of replacing the **null** value with **0** for `is_result = 'False'` during data preprocessing as having `'False'` denotes the failure of the searching process for bus rides.
<br>


  -  high_demand_val<br>
  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/cbfe31da-3a67-4b1e-a823-fb40d372cb51)

   > The `high_demand_val = '0'` has the highest counts, probably because there are too many missing values before data preprocessing.
<br>
  
 -  user_device_os
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/22ea30f3-1cd0-4b52-b002-5a0f05e4b138)

 > Android contributes **81.2%** of the overall user device operating system, whereas ios only has **18.8%** of the overall user device operating system.
<br>


  - user_device_app_version<br>
  
  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/9f7489ad-6a8b-44db-b690-e99fea943b82)
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/be2456e4-146e-4685-a141-569ff32a4662)

   > As there are too many different app version numbers, displaying the top five app version numbers used in searching for bus rides would be helpful for determining the most widely used user device app versions in the context of searches for bus rides. From the visualization, it is observed that `user_device_app_version` with a '**2xx**' value is the preferred `user_device_app_version` for the bus ride app platform among New Yorkers.


### Feature Engineering  <a name = "fe"></a>
1. Extracting data like hour, month and year from the `search_time`.
   ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/cfe344ca-86c2-4727-96e5-7e7d80352e53)

> From the count plot above, it can be concluded that 3 p.m. is the peak hour for searching for bus rides, as the number of searches at that time is the highest.

2. Creating a new feature `total_walk_time` with the summarization of the `median_pickup_walk_time` and `median_dropoff_walk_time`.
   ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/e7fcf564-b683-447a-9273-95271e1237b2)

3. Creating a binary feature `is_high_demand`, indicating whether there is high demand.
  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/d58e1ef6-07bc-408c-83dc-47041939ab9d)

### Correlation  <a name = "corr"></a>
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/91d25f30-f338-4df2-8649-16f357e9c2df)
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/9d456d68-ff22-4095-a3e2-d59b3e07cd05)

The darker the cell colour, the higher the correlation between the numeric variables.

##### Bivariate analysis  <a name = "bi_var"></a>
- user_device_os & is_result<br>

  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/2fb745a2-71a8-4f3c-a262-d5fdfaf0616f)
  <br>
   #### **Insights:**
   > Android contributes the most to the user's device operation system used in searching for bus rides. This reveals that Android is the operating system of choice for New Yorkers over iOS. However, no matter 
   the type of user device operating system, there are times when searches are not successful.
  <br>

- user_device_os & num_of_results <br>
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/55f6594e-91ce-4fed-aba2-c86bee09b561)
  <br>
   #### **Insights:**
   > The box plot for `user_device_os = ios` has only one line and outliers on both sides, indicating that there are outliers or extreme values in the dataset but that the data is generally homogeneous 
     inside the central 50%. Meanwhile, the box plot for `user_device_os = android` suggests higher variability and the majority of the data is within the box and whiskers.
<br>

- search_month & is_high_demand <br>

  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/ca498b58-84c5-4b75-a8f5-03e0f9991c16)
  <br>

    #### **Insights:**
    > November is the month when many New Yorkers utilize bus rides, as shown in the histogram above. However, it also contributes to the highest counts of low demand, which means there are higher possibilities 
    of having seats available at certain times compared to other months.
<br>

- user_device_app_version & is_high_demand <br>

  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/ae3a6a96-a979-4c13-ad89-da9483128853)
  <br>
  
    #### **Insights:**
    > According to the count plot above, it can be concluded that the `user_device_app_version = '286'` is the best app supported version by referring to the counts of bus seat availability demand because the 
    counts also represent the number of successful searches for bus rides.
<br>

- median_pickup_walk_time & median_dropoff_walk_time <br>

  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/3d287caa-ad39-466a-856f-b957c2a69bd2)
  <br><br>
   #### **Insights:**
   > This might point to situations where users have longer drop-off walks but shorter pickup walks, possibly as a result of particular features of the pickup sites or routes.
<br>

- is_high_demand & total_walk_timev <br>

  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/6ba834a3-5bb3-4b01-bee2-04ed1bea269e)
  <br>
    #### **Insights:**
    > It demonstrates that **total walking time**—the estimated amount of time a user spends walking in both directions (to anf from bus stations) will somewhat **increase** in situations where there is a **high demand for bus seats**.
<br>

- user_device_os & user_device_app_version <br> <br>
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/72d4b369-8444-4f25-84bf-157de3ae808a)
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/3e72ac26-0b8e-4666-a7e5-547608c4f660)
    #### **Insights:**
    > From the bar chart above, it is observed that the top 5 app versions for iOS devices start with the value of *'3xxx'*.
 <br>
 
- total_walk_time & median_bus_travel_time <br>

  ![image](https://github.com/drshahizan/Python_EDA/assets/146581747/7fb4951c-d695-4c2f-83c6-7a795a57831e)
  <br>
    #### **Insights:**
    > Certain locations may have efficient bus routes, leading to shorter total walk times and vice versa. This could indicate that not every area has similar variations in the efficiency of bus routes.
<br>

- search_id & is_high_demand <br> <br>
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/5af95841-09e0-411b-babf-5d6a8ca28cb2)
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/e9d9a092-875b-4310-b098-c3462823c46a)
![image](https://github.com/drshahizan/Python_EDA/assets/146581747/9c44724a-37be-48a2-a16b-6b2175c83349)

    #### **Insights:**
    > Based on the line plot, the search frequency is said to be influenced by the high demand frequency. More searches lead to a higher demand frequency, resulting in no available seats.
 <br>
    
## 6. Conclusion <a name = "conclusion"></a>
**The key findings/insights gained from this EDA:**
-  New Yorkers prefer using **Android** compared to iOS when searching for bus rides. This could give an insight into the development of the application platform and focus further development mainly on Android compatibility and user experience. Despite that, the presence of **unsuccessful searches across both Android and iOS** indicates that search success is **not solely dependent** on the **user's operating system**.

- **iOS** users might have **more consistent search** success rates, while **Android** users would see a **greater variety** of search results.

- **November** is a month when a **lot of people in New York take buses**, as the histogram's high counts show. This could be due to various factors, including the season, the weather, events, and holidays. There are also certain days or situations where demand is reduced, which gives the overall impression that not every day the bus is fully occupied.

- The **peak hour** for bus rides, observed to be at **3 p.m.**, signifies a period of **heightened demand and potential congestion within the bus transportation system in New York**. This information is crucial for both commuters and bus companies to maximize the transportation experience in New York. 

- There seems to be a **relationship between total walking time and high bus seat demand (`is_high_demand`)**. The **`is_high_demand`** also denotes that the city is **busy or crowded with people**, which is why people may have to take **longer walking durations**.

- There might be certain specific areas with **different variations in the efficiency of bus routes (higher or lower)**.

- The finding that specific searches tend to happen more frequently during periods of high demand is essential for customized recommendations and focused interventions.
  
## Contribution 🛠️  <a name = "contribution"> </a>
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

