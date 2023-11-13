## Pandas-Profiling Automated EDA for Dataset Analysis

![image](https://github.com/drshahizan/Python_EDA/assets/118237681/dc632518-2ae2-4f52-9015-62a5b04c1a89)



Pandas Profiling is a Python library that simplifies and enhances exploratory data analysis (EDA) on a dataset through integration with the Pandas library. It produces a detailed HTML report containing diverse visualizations and insights, aiding in the comprehension of your data's organization, distribution, and interdependencies.

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | :-------------: |
| LIEW YVONNE            |A21EC0045      | CS1    |
| MUHAMMAD HARITH HAKIM BIN OTHMAN              |A21EC0205     | CS2A    |
|NADIA SYAFIQAH BINTI ZULKIPLI|A21EC0098      | CS2B   |
| ALYA BALQISS BINTI AZAHAR              |A21EC0158      | CS2C    |

# HOSPITAL CASE STUDY USING PANDAS PROFILING EDA
The dataset is about the number of peoples that are admitted in the hospital during the COVID-19 Pandemic in each of the state in Malaysia. The data set is from GitHub dataset. We are trying to analyse the correlation of the availability the beds and number of occupied beds for COVID-19 patient. We also using the Pandas Profiling EDA to generate a dashboard.

## 1. Selecting Automated EDA Tools



*   Pandas-Profiling is a Python library that provides an easy way to perform automated exploratory data analysis (EDA) on a DataFrame using the popular Pandas library. It generates a detailed profile report that includes a variety of statistics, visualizations, and insights about the dataset. Here's a brief overview of the key features of pandas-profiling:

![image](https://github.com/drshahizan/Python_EDA/assets/118237681/38fd7998-cf68-40a4-b761-a3aeff749e38)


## 2. Malaysian Dataset


*   The dataset is from GitHub and can be reviewed at /content/drive/MyDrive/Colab Notebooks/DATASET/hospital.csv.

![image](https://github.com/drshahizan/Python_EDA/assets/118237681/9075625a-6f4e-4886-9004-63212352ca42)


## 3. Data Preparation

Load Dataset using Pandas to check whether the dataset is good and clean to be used for analysis

The dataset has been downloaded and extracted.

![image](https://github.com/drshahizan/Python_EDA/assets/118237681/1c3f4408-0c37-4ff4-ba8a-61aa6b8f7ee6)

![image](https://github.com/drshahizan/Python_EDA/assets/118237681/3f67a40c-cac8-44c6-96d5-0a58455b97b9)


## 4. Implementation of Automated EDA Tools



*    **Loading dataset into the tool**

This Python code leverages the pandas_profiling library to create a detailed profiling report for a pandas DataFrame (df), titled "Hospital Dataset Profiling." Using the ProfileReport class, the analysis is encapsulated in a profile object, providing insights into data types, missing values, and summary statistics. This report offers a swift and comprehensive overview of the dataset's key characteristics.


![image](https://github.com/drshahizan/Python_EDA/assets/118237681/52f45b6e-ed19-4176-b525-6686f09c2829)

*   **Generate basic statistics and visualizations.**

By calling 'profile' the tool whill generate a dashboard containing reports of the dataset.


![image](https://github.com/drshahizan/Python_EDA/assets/118237681/11ed94bc-7453-49f9-ba02-994a68d7b0d0)

*   **Explore relationships and patterns in the data.**

After the dashboard has been created. We can scroll down the dashboard to see the correlation and interaction between different variables for us to make conclusion pr insight of the dataset.



*   **Unique features or capabilities of each tool that you find noteworthy.**

The HTML report is interactive, enabling exploration of visualizations, collapsing sections, and filtering data. Pandas-profiling offers in-depth analysis for categorical data, showcasing unique values and visualizations. The tool also provides visual insights into missing values, aiding in identifying patterns in the data gaps.

## 5. Pros and Cons Analysis

**PROS**

* **Accessible to Users**:
Straightforward for individuals accustomed to Pandas, necessitating minimal coding for thorough analysis.
* **Graphical Representations**:
Incorporates an extensive array of visualizations, simplifying the comprehension of data distribution and relationships.


**CONS**

* **Restricted Statistical Analysis**:
Although it furnishes descriptive statistics, it does not perform hypothesis testing or statistical inference.
* **Restricted Customization**:
Despite offering substantial information, the extent of customization for the generated report is somewhat constrained.

**INSIGHT**


*  Using Pandas-Profiling, can help us do fast-generated profiles and analysis of datasets from scratch. Sometimes it can be hard to load the dataset from the file to the tool, but in the end with some help from resources we manage to load the dataset and do our findings from the data. If the data is not clean before we use the tool, the profile will show some uncertainties and errors that will make our profile more hard to read, and so on.


## 6. Conclusion

Here are some conclusions from the analysis of the dataset using the EDA tool:


*   The number of beds with a patient who has COVID-19 is decreasing by under 1000 beds throughout the states in Malaysia.
*   Sabah has now the most number of COVID-19 hospitals with 161 hospitals, compared to Perlis with 7 COVID-19 hospitals according to this dataset.
* Kelantan has the highest number of people who are admitted to the hospital because of COVID-19 with a total of 15 people.


**RECOMMENDATION**

Pandas-profiling is suitable to handle a medium-sized dataset to be performed with analysis and profiling faster and in a short medium of time. The dataset needed to be in specific term so that the user or the person who will perform the analysis knows what the dataset is about and understand what is to be analyzed later. This EDA tool makes it easy to understand the profile or analysis that will be generated later, but with a bit of data cleaning, the analysis will be smoother and understandable for later use.

## 7. Referrences


*   [Generate Report Using Pandas-Profiling](https://www.analyticsvidhya.com/blog/2021/06/generate-reports-using-pandas-profiling-deploy-using-streamlit/)

* To see more of the analysis, you can visit my [GOODLE COLLAB!](https://colab.research.google.com/drive/1bjXdLrLQNeAkFsR1CXL-kjzTHah7vjAw#scrollTo=6Xq-TV0ifJpG)




