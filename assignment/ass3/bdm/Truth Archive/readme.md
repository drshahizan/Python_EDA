# Assignment 3: Big Data EDA
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]( https://colab.research.google.com/github/drshahizan/Python_EDA/blob/main/assignment/ass3/bdm/Truth%20Archive/ass3.ipynb)
</br>
Open in GitHub: <a href="https://github.com/drshahizan/Python_EDA/blob/0d18332ff234ae9ec1b9e07fef9c327d6f49d767/assignment/ass3/bdm/Truth%20Archive/ass3.ipynb" ><img src="../../../../images/answer.png" width="24px" height="24px" ></a> 
## Group members:
| No | Name |  MatricNo | 
| -----: |  ------ | :-----: | 
|1        |Hazem Fenneer   |MCS231019         |
| 2       |Shivanesh       |MCS231014         |
|   3     |Nur Shahirah    |MEC233005         |
|     4   |Mustafa         |MCS212012         |

## Introduction
The analysis and prediction of taxi trip data in New York City serve as a compelling domain for data science projects. In this project, our focus lies on Exploratory Data Analysis,  the crucial process of conducting preliminary research on data using graphical representations and summary statistics in order to identify patterns, identify anomalies, test hypotheses, and verify presumptions. This particular dataset contains data on taxi rides in New York City in 2015, making it a valuable resource for exploratory data analysis.

The dataset consists of various attributes such as vendor ID, pickup and dropoff timestamps, passenger count, trip distance, geographical coordinates of pickup and dropoff locations, fare details, payment type, and additional charges. In order to improve exploratory data analysis (EDA), our project will develop new features that will record important data.

## Task Overview
1. **Dataset Selection**: Your first task is to select a suitable dataset for this assignment. You can choose a dataset from various sources, such as Kaggle, UCI Machine Learning Repository, or any other relevant dataset source. Make sure the dataset is in a format that can be easily loaded into Google Colab.

2. **Loading the Dataset**: Use Python libraries like Pandas to load the selected dataset into your Colab notebook. You can upload the dataset from your local machine or load it directly from an online source.

3. **Exploratory Data Analysis (EDA)**: Perform exploratory data analysis to understand the dataset's characteristics. This includes checking for missing values, understanding the data types, and getting a sense of the dataset's structure.Perform Univariate Analysis followed by Bivariate Analysis. Things we were able to find doing EDA on the chosen dataset:
* The Dataset contains 12748986 rows and 19 columns.
* All the columns had zero missing values except for improvement_surcharge, this column had 3 missing values.
* None of the columns contain mixed types.
* 383 duplicate rows were found and removed.
* We've observed that there are only two vendors (Vendor 1 and Vendor 2). Both vendors have nearly equal trip shares, with a minimal difference between them. However, Vendor 2 is noticeably more renowned among the population, as indicated by the graphs provided.
* We see that the mostly 1 to 6 passengers avail the cab. The instance of large group of people travelling together is rare.
* We can observe that most of the trips took 0 - 30 mins to complete.
* Coverted these dates into days of the week so a pattern can be found. Most trips were taken on Saturday and the least amount of trips were taken on Monday
* Since it is difficult to analyze the time component when it is represented in hours, minutes, and seconds, we split the times into four time zones: morning (4 hours to 11 hours), midday (10 hours to 16 hours), evening (16 hours to 22 hours), and late night (22 hours to 4 hours). Thus, we see that evenings are when most pickups and drops happen. whereas the morning and late night hours see the fewest drops and pickups.
* There are significantly more N flags.
* The payment types are mostly 1 and 2. 1 represents cash money and 2 for online payment. Its evident that most customers prefer cash pay.
* There are 79365 trip records with 0 miles distance.
* Majority of rides are completed in the range of one to ten miles, with some spanning up to thirty miles.
* There should have been a linear relationship between the distance covered and trip duration on an average but we can see dense collection of the trips in the lower right corner which showcase many trips with the inconsistent readings.
* The Pickup plot indicates that the majority of the spread is centered in the Manhattan region. For a pickup location, Manhattan is fairly populated, we can say. In contrast to the pickup zone, the drop zone is fairly dispersed. The average distance, as determined by distance analysis, is 2.1 miles, which helps to explain why Manhattan has experienced a significant intensity drop.

4. **Visualization**: Visualize the transformed data to gain insights into feature distributions and relationships.

5. **Feature Creation**: If new features can offer useful information, then make them. This could entail creating new features based on domain expertise or combining or aggregating already-existing ones.

## Conclusion 
In summary, the NYC taxi trip dataset's EDA has revealed important information that can be used to support data-driven decision-making. Predictive modeling and machine learning algorithms, among other forms of further analysis, could be used to uncover more subtle patterns and trends, which would ultimately enhance New York City's urban mobility and taxi services.

