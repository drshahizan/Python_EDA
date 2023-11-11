# D-Tale

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/4871d9e0bbcfc53b0ef7ae24f80d8fdbf7776bcb/assignment/hpdp/BERUK/case_study2c/img/dtale.png" width=500>
</p>

D-Tale is an Exploratory Data Analisys tools that combines a Flask backend and a React front-end to provide an easy method to examine and analyse Pandas data structures. It works perfectly with ipython notebooks and python/ipython terminals. This tool now supports Pandas objects such as DataFrame, Series, MultiIndex, DatetimeIndex, and RangeIndex.

## a. How to load the dataset into the tool.
To load a the data into D-tale, follow these step 

### Step 1 : install D - Tale

 ```python
      !pip install dtale
 ```

### Step 2 : import all necessary package
 
 ```python
      import pandas as pd
      import dtale
 ```
If you are using it on google colab, please include the following line
 
 ```python
      import pandas as pd
      import dtale
      import dtale.app as dtale_app

      dtale_app.USE_COLAB = True
 ```
### Step 3 : load dataset

 ```python
     data = ' ' #data directory
     df = pd.read_csv(data) #read_csv is used to read csv files, use proper function based on your dataset file type   
 ```
### Step 4 : load dataset into Dtale

 ```python
     dtale.show(df) 
 ```
### Output 
The link should bring you to the following page :

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/4871d9e0bbcfc53b0ef7ae24f80d8fdbf7776bcb/assignment/hpdp/BERUK/case_study2c/img/Screenshot 2023-11-10 171250.png" width=800>
</p>

The data displayed should be based on the data you used.
If you are using jupyter notebook, the page will be opened in the output column. to open it in new tab, click the dtale loog and select ' 'open in new tab' 

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Describe (5).png" width=800>
</p>

## b. How to generate basic statistics and visualizations.
D-tale provide some basic statistic and visualization on the data of each column. To use this function, follow the following steps : 

### Select a column, right-click and select Describe (column analysis)
<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Describe.png" width=800>
</p>

The output should be something like this
<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Screenshot 2023-11-10 171351.png" width=800>
</p>

As you can see, this feature describe basic statistical feature of the column such as mean, median, mode, the quartiles and it also record all missing values that the column have, and also list all the outliers

If you select histogram function on the top bar, there will be a histogram shown that shows the relationship between the values and bin, with a KDE graph

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Describe (1).png" width=800>
</p>

## c. How to explore relationships and patterns in the data.
There are two ways to find relationship and pattern in data,  first is correlation and by creating charts

### Correlation
To see the correlation between the column, go to visualize and select correlation

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Describe (2).png" width=800>
</p>

It will open a side bar titled Pearson Correlation Matrix such as below

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Screenshot 2023-11-10 172000.png" width=800>
</p>

These Correlation matrix will show all the correlation between all possible pair of variable (column) to summarize large dataset, find possible pattern and to make decision

### Charts
To make a chart in D-tale, go to visualization and select "Chart"

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Describe (2).png" width=800>
</p>

And it should open a new browser such as following

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Screenshot 2023-11-10 171742.png" width=800>
</p>

You can design any chart based on the option given, but for this example, we will make a bar chart to visualize the relationship between a certain collumn. Follow the following steps in the diagram below :

<p align="center">
    <img src="https://github.com/drshahizan/Python_EDA/blob/68eb59807192021d56d8963aa0b944a32804b6ec/assignment/hpdp/BERUK/case_study2c/img/Describe (3).png" width=800>
</p>

The output will be displayed in the same page. 

## d. Unique features and capabilities of D-Tale .

