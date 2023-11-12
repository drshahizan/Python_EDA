# Assignment 2 - Case Study 2a - SweetViz
<a href="Assignment_2_Case_Study_2a.ipynb"
   target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="CASE_STUDE 2a"/></a>

TODO - Write some introduction about your project here: describe the dataset, where you got it from, what you're trying to do with it, and which tools & techniques you're using. Please provide your group member name and their matrix number.

|    Name           |           Matric Number       |                      
|-------------------|-------------------------------|
|Muhammad Fikri Bin Sharunazim    | A21EC0075       |
|Muhammad Farhan Bin Ibrahim|        A21EC0072      |
|Muhammad Adam Fahmi Bin Mohd Taufiq |A21EC0061|
|Mikhail Bin Yassin |A21EC0053                      |

---
# Overview
## Malaysian COVID-19 Dataset

The **Malaysian COVID-19 dataset** provides comprehensive information related to the COVID-19 pandemic in Malaysia. It covers various aspects, including daily recorded cases, clusters, testing data, healthcare facility utilization, deaths, and vaccination statistics. Specifically, the dataset includes the following key components:

1. **Cases**: Daily recorded COVID-19 cases at both the country and state levels.
2. **Clusters**: Exhaustive list of announced clusters with relevant epidemiological data points.
3. **Tests**: Daily tests (note: not necessarily unique individuals) categorized by type at both country and state levels.
4. **Healthcare**: Information on patient flow to and from COVID-19 Quarantine and Treatment Centers (PKRC), hospitals, and ICU bed capacity and utilization.
5. **Deaths**: Daily deaths due to COVID-19 at both country and state levels.
6. **Vaccinations**: Daily and cumulative vaccination data, including dose type, brand, and coverage at country, state, district, and demographic levels.

## Data Source

The dataset is sourced from the **Ministry of Health Malaysia (MoH-Malaysia)**. It is maintained and updated by various entities, including CPRC, CPRC Hospital System, MKAK, and MySejahtera.

## Purpose and Goals

The primary objective of analyzing this dataset is to gain insights into the COVID-19 situation in Malaysia. Researchers, policymakers, and the public can use this data to monitor trends, assess the impact of interventions, and make informed decisions. Specific goals may include identifying patterns, predicting case trajectories, assessing vaccination coverage, and understanding healthcare resource utilization.

## Tools and Techniques

- **Python Libraries**: Pandas, NumPy, and Matplotlib/Seaborn for data manipulation, exploration, and visualization.
- **Jupyter Notebooks**: To document analyses, visualize data, and share insights.
- **Statistical Methods**: Descriptive statistics, time series analysis, and regression modelling.
- **Geospatial Analysis**: If geographical data (such as state or district-level) is involved.

Additionally, machine learning techniques can be applied for predictive modelling or clustering if needed.

For more details, you can explore the official COVID-19 dataset repository maintained by MoH-Malaysia.

---

## Downloading the Dataset

### Links of Dataset  
Cases by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/cases_state.csv  
Death by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/deaths_state.csv  
Vaccination by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_state.csv

---

## Data Preparation and Cleaning

Install SweetViz by running this code below


```
pip install sweetviz
```

Install pandas and sweetviz

```
import pandas as pd
import sweetviz as sv

cases = pd.read_csv(' https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/cases_state.csv') #Cases
death = pd.read_csv('https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/deaths_state.csv') #Death
vax = pd.read_csv('https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_state.csv')   #Vaccination
```

Call table for cases
```
cases
```

Call table for death
```
death
```

Call table for vax
```
vax
```

Merge all of the table to create one set of data (Inner Join)
```
df = cases.merge(death,on=['date','state']).merge(vax,on=['date','state'])
df_row, df_cols = df.shape
```

To see all the info data types of our table columns, we run
```
df.info()
```

To handle missing values, we can first check for each of the columns, we run
```
df.isnull().sum()
```

---
## Implementation of SweetViz
First we assign a new variable to generate our SweetViz report
```
report = sv.analyze(df)
```

Then, we can explore pattern and demographic info from SweetViz tool, we run
```
report.show_html('SweetViz_Report.html') #show report
```

To get the generated report of SweetViz, we can go to the files on the google colab
<p align="center">
    <img src="https://raw.githubusercontent.com/drshahizan/Python_EDA/main/assignment/hpdp/Pergolakan/case_study2a/SweetViz1.png" width=1000>
</p>

Download the SweetViz_Report.html then, open the html file. 

---
## Insight SweetViz on **Malaysian COVID-19 Dataset**

EDA on SweetViz will display rich visualisations, for example:
<p align="center">
    <img src="https://raw.githubusercontent.com/drshahizan/Python_EDA/main/assignment/hpdp/Pergolakan/case_study2a/SweetViz2.png" width=1000>
</p>

To check the association of our data, click the association button inside the DataFrame box
<p align="center">
    <img src="https://raw.githubusercontent.com/drshahizan/Python_EDA/main/assignment/hpdp/Pergolakan/case_study2a/SweetViz3.png" width=1000>
</p>

---
## Pro and Cons Analysis

### **Pros**

1.   **Automated Report Generation:** Compared to manually developing visualisations, Sweetviz saves time by automating the process of generating an extensive EDA report.
2.   **User-Friendly:** Sweetviz's basic API makes it very simple to use, catering to customers with different degrees of experience in data analysis.
3.   **Rich Visualisations:** Sweetviz offers a wealth of insightful and rich visualisations, such as scatter plots, histograms, and other visualisations that aid in comprehending data distribution and variable interactions.


### **Cons**

1.  **Overwhelming Output:** Sweetviz can occasionally provide an excessive amount of visualisations, particularly for huge datasets. Going through each visualisation and gleaning important information might take some time.
2.  **Limited Interactivity:** There are no interactive elements and the visualisations are static. If you like using interactive graphs to explore data, this might be a drawback.
3. **Not Suitable for Big Data:** Sweetviz may not be the most effective tool for really large datasets because it can take a lot of resources to generate visualisations for such enormous volumes of data.

---

## Conclusion

Using Sweetviz on our Malaysian COVID-19 dataset for Exploratory Data Analysis (EDA) provides a quick and visually rich overview of key insights. Sweetviz simplifies the analysis process, automating the generation of comprehensive reports that include detailed visualizations. It enables us to efficiently explore the distribution of COVID-19 data, identify potential patterns, and compare different aspects of the dataset. However, it's essential to complement Sweetviz with other statistical analyses to ensure a thorough understanding of the dataset, especially considering the dynamic and complex nature of pandemic data.

Sweetviz serves as a valuable starting point for EDA, offering accessibility and ease of use, but users should be mindful of its limitations and consider integrating it into a broader analytical toolkit for a more nuanced interpretation of our Malaysian COVID-19 dataset.
