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
*   Once the report have been created, simply pass it into the **show_html()** functions.
*   Open the SweetViz html report to explore the relationships and patterns.
```
report.show_html('SweetViz_Report.html')
```

*   Explore the correlations.
```
report_correlation = sv.analyze(df, pairwise_analysis='on')
report_correlation.show_html('Correlation_Report.html')
```
