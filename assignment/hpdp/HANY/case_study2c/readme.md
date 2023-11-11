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

# 📚 Case Study 2c: Automated EDA Tools (Lux)
## 1. Download the dataset
Download the Malaysian dataset named "hospital.csv" from the following URL:<br>
   https://github.com/MoH-Malaysia/covid19-public/blob/main/epidemic/hospital.csv
  <div align="center"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/30164b12-dd5a-41ed-be36-d04b43d5368b" width="800"></div>
  <div align="center">Sample of dataset</div><br>
 

## 2. Install Lux
Install the automated Exploratory Data Analysis (EDA) tool Lux by using the following code:
 <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/99cbe226-c6da-4c2e-b001-aa42ba52934b" width="300"></div><br>

## 3. Load the dataset
 **3.1 Import necessary libraries**
 <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/2e56c2b5-f1b2-4e67-a637-c61a50420736" width="300"></div>
 
 - **lux**: This library is for interactive visualizations and exploratory data analysis (EDA).
 - **pandas**: A powerful data manipulation and analysis library in Python.
    
**3.2. Enable custom widget manager in Google Colab**
    <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/5709ce11-11ee-414b-bf06-993cfdfe2c57" width="450"></div>
  This enables the custom widget manager in Google Colab. Widgets are interactive elements that can be used to enhance the user interface when working with data.

 **3.3. Load the dataset**
 <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/c022fa7c-9577-4ed2-b696-b4ba3a3e6f11" width="900"></div>
 
   This is a pandas function used to read data from a CSV (Comma-Separated Values) file and load it into a pandas DataFrame.
   It assigns the loaded dataset to a variable named **"df"**
    
 **3.4 Data Manipulation**
    <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/b8b00b6c-5e5a-4e5f-86c3-5df6ea086eb9" width="550"></div>
    
  This step called "Converting a Column to Datetime." Specifically, it converts the 'date' column in the DataFrame (df) from its current data type to the datetime data type. It is essential to prevent temporal errors.
  - **df['date']**: Selects the 'date' column from the DataFrame df.
  - **pd.to_datetime()**: Pandas function that converts the argument to datetime.
  - **format='%Y-%m-%d'**: Sets the format of date column to year-month-day (e.g., '2023-11-11').
<br>

## 4. Generate Statistics and Visualisations
### 4.1 Display the dataframe

<div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/282d4415-cb2f-4344-bb2f-91af855cc9ff" width="150"></div>
Output:
<div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/531d3335-8bfc-437e-b0fd-ab3af7b5296b" width="1000"></div><br>

### 4.2 Visualisations
**4.2.1 Automatic visualisations**
- Press Toggle Pandas/Lux located on the top left of the Dataframe to automate visualisations.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/33d0a468-f54d-4664-a01f-805cd42a6b70" width="500"></div>
- Output:
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/5b7122e7-ad7e-4b24-9183-60751331d03a" width="1000"></div><br>

**4.2.2 Interactive Table**
- To convert the Dataframe into an interactive table, press the table icon on the right of the Dataframe.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/7668babf-2ef0-48ff-87ac-f9bd93c0b2dd" width="400"></div>
- Output:
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/9360a7c4-6ea0-4b71-9d71-77ff7837480e" width="900"></div>
- There is a filter option that accepts index as input to narrow down the targeted data points.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/a1b12b7a-f6c5-4e7a-b9af-f97c436e3e71" width="300"></div>
- Output:
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/2028329c-521f-4aa4-a5d4-b9c3f04ca96d" width="900"></div>
- Navigate between pages by selecting the page number located at the bottom right of the DataFrame.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/622f1ec8-4530-4a53-80d9-1ef5fba8fbf0" width="300"></div>
- The option to specify the number of displayed records per page, with choices of 10, 25, 50, or 100, is available at the bottom left of the DataFrame.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/209fdd43-27d2-4a96-aea4-9677c13f2f04" width="300"></div><br>

**4.2.3 Chart Recommendations**
- To access chart recommendations, select the chart icon situated to the right of the DataFrame.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/9d3addc4-e025-4194-912b-96c8084c9b73" width="300"></div>
- A variety of charts will be presented for the user's selection.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/d8ac2313-7a33-4fd4-a93f-d838bb944130" width="500"></div>

- Once a chart is chosen, a corresponding block of code is generated automatically for displaying the selected chart.
- Example:
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/5da94747-f831-40a3-9dd1-1c8492f06579" width="600"></div><br>

## 5. Explore Relationships and Patterns
Utilise Lux by exploring its functions to create relationships and patterns with targeted variables.

### 5.1 Visualisation List
One way to explore the relarionships is by using the **Vis class**.
<div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/3ad7b7ed-71c0-44e4-b271-523cfabcb5db" width="300"></div><br>

- This code creates an individual visualisation focusing on the "state" of Johor and the "hosp_noncovid" column in the DataFrame.<br>

Another way to explore relationships is by using the **VisList class**.
<div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/f8dde494-db35-441e-980d-8a80d1b73f2d" width="900"></div><br>

- This code generates a list of visualizations, exploring the relationship between "state" and "admitted_total" with a focus on filtering based on the "state" column.<br>
  
### 5.2 Grouped Statistics
An example of analysing grouped statisticsis by using the **groupby** method.
- This code example groups the DataFrame by the "state" column and calculates the mean for each group.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/85a3147e-1606-482d-aeff-7069c29d6e61" width="900"></div><br>
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/eff2ea91-b637-45cf-a6c6-269d89e9eb46" width="900"></div><br>

In Lux, the **"Enhance"** and **"Generalize"** options are features designed to assist users in the exploratory data analysis process.
- **Enhance:**
  - focused on providing additional insights and details related to a specific aspect of the data.
  - offers relevant visualizations or statistical measures that are specifically tailored to selected attributes.
- **Generalize:**
  - provide a broader overview or summary of the entire dataset.
  - helps users to understand general patterns, trends, or key statistics without necessarily focusing on a specific attribute.

### 5.3 Specification
An **"intent"** is a way to specify targeted attributes and analyse their relationship. It also guides Lux in generating relevant visualizations and insights.
<div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/1968605d-a2c0-404a-ba20-353144b720cf" width="500"></div>

- It sets the intent for the DataFrame df to focus on specific attributes. In this example, it focuses on **"admitted_covid"** and **"discharged_covid".**
- Output:
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/dee4d034-32db-4051-a048-2f8c580e6415" width="900"></div>
- The **"Filter"** option filters and generates the charts accordingly. In this case, it filters the data on **"admitted_covid"** and **"discharged_covid"** by **"state"**.
- The **"Generalize"** option produces a summary on the targeted attributes. In this case, it illustrates the number of records of **"admitted_covid"** and **"discharged_covid"**.

### 5.4 Export
There is function to extract a visualization from a Lux DataFrame.
<div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/da4f773c-ab90-4fb9-9996-f77929a1cf32" width="900"></div>

- Select a chart from the Dataframe for export.
- Click the icon at the top-right of the widget. A blue order with a check mark will appear once a chart is selected.
- Execute the following code to extract the chosen chart.
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/653b604d-3111-4264-99c4-ae32f1f82054" width="300"></div>
- The exported attribute typically stores a list of visualizations generated during the exploration process.
- **[0]** indicates that the first visualization from the list is retrieved. Lux stores visualizations as a list, and this indexing selects a specific visualization.
- This code allows users to access and work with a specific visualisation that was generated. It's useful for users to manipulate or analyse a particular visualisation in more detail or incorporate it into a custom analysis or report.
- The extracted visualization is then assigned to the variable vis.
- Output:
  <div align="left"><img src="https://github.com/drshahizan/Python_EDA/assets/121602362/a1aa4941-0047-4e36-a200-338b4467382c" width="300"></div>

## 6. Unique Features
The distinctive features of Lux have been highlighted earlier, encompassing the interactive table, chart recommendations, and the export function.

- **Interactive Table**
   - Lux transforms the loaded DataFrame into an interactive table, providing a dynamic and user-friendly interface for exploring data.
   - Enables users to interactively sift through and visualize data directly within the notebook environment.
   - It allows users to explore their data by filtering, sorting, and selecting subsets of the data, saving time and effort compared to manually exploring the data.
     
- **Chart Recommendations**
   - Lux offers automated chart recommendations based on the selected attributes based on the user's intent, streamlining the process of visual exploration.
   - Saves time by automatically suggesting relevant visualizations, aiding users in identifying relationships, patterns and trends.
   - It automatically fills in the missing details and determines appropriate visualization mappings.
     
- **Export Function**
   - Lux also provides an export function to save, share, and utilise selected visualisations generated during data analysis.
   - Allows users to capture and integrate specific visualisations into reports or presentations.
     
## 7. Pros and Cons of Lux

## 8. References


