# Assignment 2
# Case Study 2a

### Group Name: DEADPOOL
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| MUHAMMAD AMIR JAMIL BIN JAMLUS | A21EC0202   |
| KEE SHIN PEARL             | A21EC0190  |
| MUHAMMAD IZZUDDIN BIN SHABRIN |A21EC0083  |
| UMAR HAZIQ BIN MUHAMAD NORHISHAM | A21EC0235     | 

<br>

## Table of Content
1. [Introduction](#introduction)
2. [Dataset Information](#dataset-infomation)
3. [Exploratory Data Analysis](#exploratory-data-analysis)
4. [EDA Tool - D-Tale](#eda-tool)
5. [Exploratory Analysis and Visualization](#exploratory-analysis-and-visualization)
    * [Descriptive Statistics](#descriptive-statistics)
    * [Correlation Analysis](#correlation-analysis)
    * [Data Visualizations](#data-visualizations)
8. [Inference and Conclusion](#inference-and-conclusion)
9. [Reference](#reference)

## Introduction

## Dataset Information

In this assignment the Malaysian dataset is provided by the Ministry of Health of Malaysia(MOH) and was downloaded from the offical github site of the MOH.

[Blood Donation Malaysia](https://raw.githubusercontent.com/MoH-Malaysia/data-darah-public/main/donations_state.csv)

<br>

## Exploratory Data Analysis

Exploratory Data Analysis (EDA) involves the investigation and examination of datasets to discover patterns, trends and gain insights. Through visualization techniques and statistical summaries, EDA is the foundational work for understanding data characteristics and informing subsequent analysis or modeling processes.

<br>

## EDA Tool - D-Tale

This study case will be using D-Tale for EDA tool. D-Tale is an interactive and user-friendly Python library that assist users in Exploratory Data Analysis (EDA). It offers a web-based interface to explore and analyze dataframes, providing features like filtering, sorting, statistics, and visualization, making it intuitive for data exploration and gaining insights within Google Colab environment.

To integrate D-Tale into a Python environment, the first thing is to install the D-Tale library. It can be installed using

```python
pip install dtale
```

<br>

Import the nessasary libraries need from D-Tale and launch D-Tale to create an interactive web-based interface. 

```python
import dtale
import dtale.app as dtale_app
```

<br>

Set USE_COLAB to true to be able to use D-Tale within the google colab environment.

```python
dtale_app.USE_COLAB = True
```

<br>

By using the dtale.show(). A link will be generated as the output in google colab, when clicking it will open a new browser tab with the D-Tale interface.

```python
dtale.show(df)
```

<br>

new browser tab interface for D-Tale will show the data from the connected dataframe

![Dtale1](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale1.png)


<br>


## Exploratory Analysis and Visualization

### Descriptive Statistics:

To generate the descriptive statistics of the dataset, the "Visualize" from the new browser tab of D-Tale is selected and choose "Describe" from the dropdown

![Dtale2](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale2.png)

<br>
The D-Tale will generates descriptive statistics of the imported dataset, including mean, median, mode, variance, and standard error, offering a quick summary on dataset.It will show the detailed description on the column that is selected on the right side of page.

![Dtale2a](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale2a.png)

<br>

In D-tale, the descriptive analysis of the selected column can be exported in coding by selecting the "Code Export" located on the upper right corner.

![Dtale2ex](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale2ex.png)

<br>

Date :

![Dtale2a](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale2a.png)

Daily :

![Dtale2b](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale2b.png)

donations_new :

![Dtale2c](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale2c.png)

donations_regular :

![Dtale2d](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale2d.png)


<br>

### Correlation Analysis

Back to the D-tale dashboard, from the upper part tab select "Correlation" under the "Visualize" tab.

![Dtale3](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale3.png)

<br>

D-tale will display the Pearson Correlation Matrix of the numerical variables from the imported dataset

![Dtale3a](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale3a.png)

<br>

The correlation analysis can be exported in coding by selecting the "Code Export", the popup of the code sample is shown

![Dtale3ex](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale3ex.png)

<br>

There is "Export Image" button on the upper right of the user interface, by selecting the "Export Image" button the correlation graph can be downloaded and saved in PNG file.

![correlations](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/correlations.png)

<br>

### Data Visualizations

Within the D-Tale dashboard, you can explore visualizations by selecting 'Chart' from the 'Visualize' dropdown in the upper tab. This action opens a new tab dedicated to charts where various types of visual representations of data can be created.

![Dtale4](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale4.png)

<br>

Here is the view of the new tab that is directed to create charts and visualizations based on the dataset. Users can interact with the site to plot charts, setting filters, or modify data and see the changes reflected dynamically.

![Dtale4tab](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale4tab.png)

<br>

After creating visualizations, there is the code export symbol where the code can be exported for further use.

![Dtale4aex](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale4aex.png)

<br>

When exporting images from D-Tale's charts, the output format is a PNG file which is saved during export.

![bar_export](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/bar_export.png)

<br>

The total amount of different types of blood across states :

![Dtale4a](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale4a.png)


The total amount on types of blood across the years from 2006-2023 :

![Dtale4b](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale4b.png)


Regular blood donations made by social civilian across states:

![Dtale4c]([./Dtale4c.png](https://github.com/drshahizan/Python_EDA/blob/main/assignment/ass2/hpdp/DEADPOOL%20/case_study2a/image/Dtale4c.png))

<br>

## Inferences and Summary

<br>

Pro :

* Interactive EDA tools

Dtale comes with a interactive web-based interface that is equipped with useful features that can be used during EDA. It is user friendly and it allows user to explore without extensive coding.

* Integration with Python:

D-Tale seamlessly integrates with Python, it supports python libraries like panda and numpy. This allow users to work directly with Pandas DataFramesand data manipulation workflows as it ensures compatibility between the two environments at the same time.

* Efficient Data Visualization:

D-Tale offers a wide range of charts, graphs, and plots for efficient data visualization. It also allows users to dynamically visualize and analyze data The visualization generated can provide users with a comprehensive overview of their data and gaining insights on data distributions, patterns, and outliers directly.

<br>

Cons :

* Web-Based:

Dtale is a tool that has its own web-based interface. It might not be convenient for some user as it works in 2 different environment and not just only in a python environment.

* Unfamiliar feature:

Dtale is comes with a variety of functions and tools. New user who a unfamiliar with the environment will have to spend some time to understand the different features within Dtale.

* Slowdowns:

When running large datasets with other resources at the same time, Dtale will experience some slowdown or peroformance issue.

<br>

## Conclusion

Dtale emerges as one of the functionalble EDA tools to be used as contains numerous interfaces and feature for users to explore.Especially for users that are comfortable with Python and Pandas, Dtale interactive web-based interface transforms the Google Colab environment into a site for interactive data analysis and dynamic visualization experience.Users should be mindful of when dealing with large datasets using Dtale, there might occur performance issue compared to more advanced EDA tools. Overall, the integration of D-Tale in Google Colab will provide interactive, and collaborative platform for users during data exploration and analysis.

<br>

## References

[dtale](https://github.com/man-group/dtale)

[Exploring Pandas DataFrame With D-Tale](https://www.analyticsvidhya.com/blog/2021/06/exploring-pandas-dataframe-with-d-tale/)

[Exploratory Data Analysis Using D-Tale Library](https://medium.com/@amitjain2110/exploratory-data-analysis-using-d-tale-library-261d513901fc)





