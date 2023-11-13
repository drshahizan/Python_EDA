<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 2: Exploratory Data Analysis

### Group Name: HANY
### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | :-------------: |
| LIEW YVONNE            |A21EC0045      | CS1    |
| MUHAMMAD HARITH HAKIM BIN OTHMAN              | A21EC0205     | CS2A    |
|NADIA SYAFIQAH BINTI ZULKIPLI|A21EC0098      | CS2B   |
| ALYA BALQISS BINTI AZAHAR              |A21EC0158      | CS2C    |

## 📚 Case Study 2: Automated EDA Tools (SweetViz)
This is a step-by-step guide for implementing SweetViz's **Automated EDA Tools** based on the covid-19 [hospital dataset](https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/hospital.csv).

## 1. Installation 
The installation of SweetViz is as follows:
*   The best way to install SweetViz is to use pip.
```
pip install sweetviz
```

## 2. Load the dataset into the tool
  ### 2.1 Import the necessary libraries
```
import pandas as pd
import sweetviz as sv
```

  ### 2.2 Load chosen dataset into Google Colab
```
url = 'https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/hospital.csv'
df = pd.read_csv(url)
```

  ### 2.3 Display dataframe
```
df #to display dataframe
```

  ### 2.4 Handling Missing Values
Before performing an analysis, ensure that the data is clean and ready for use.
*   To check for the missing values: 
```
df.isnull().sum() 
```

  ### 2.5 Duplicate Rows
*   To check for and remove duplicate rows if necessary: 
```
df.duplicated().sum()
```

## 3. Generate basic statistics and visualizations
*   To create the report and analyze the data, simply use **analyze()** function:
```
report = sv.analyze(df)
```

## 4. Explore the relationships and pattern in the data
*   Once the report have been created, simply pass it into the **show_html()** function:
```
report.show_html('SweetViz_Report.html')
```

*   Open the SweetViz html report to explore the relationships and patterns.
  1. On the left side of the Google Colab, click the files button.
<div align="center">
  
![c2](https://github.com/drshahizan/Python_EDA/assets/87573002/1ad533bb-265a-4b93-a18a-421c8805ce59)
**Figure 1** 
</div>

  2. Download the file, and the report preview will appear as Figure 2 below.
<div align="center">

![c31](https://github.com/drshahizan/Python_EDA/assets/87573002/c702a021-27ed-45ae-83af-53a99eefc050)

**Figure 2: The generated report of SweetViz EDA Tool.** 
</div>

*   Explore the Correlations/Association analysis.
```
report_correlation = sv.analyze(df, pairwise_analysis='on')
report_correlation.show_html('Correlation_Report.html')
```
A major source of insight and unique features of SweetViz' association graph and analysis is that it unifies in a single graph:

  1. To  analyse the associations, click **ASSOCIATIONS** button on top of the report.
<div align="center">
  
![c1](https://github.com/drshahizan/Python_EDA/assets/87573002/06d5a11c-a391-46cc-b4be-fbbf19a568f9)
**Figure 3.** 
</div>

  2. The graph will be shown in the Figure 4 below.
<div align="center">
  
![c4](https://github.com/drshahizan/Python_EDA/assets/87573002/2d3deb86-50b1-4c60-a4d3-e908e4debbc7)

**Figure 4**
</div>

Note: Squares represent categorical-featured-related variables and circles represent numerical-numerical correlations. Note that the trivial diagonal is kept empty, for clarity. 

Categorical-categorical associations (provided by the squares showing the uncertainty coefficient) are assymmetrical which means each row represents how much the row title (on the left) gives information on each column.
