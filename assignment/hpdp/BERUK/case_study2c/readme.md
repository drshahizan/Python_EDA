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
if you are using it on google colab, please include the following line
 
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

the data displayed should be based on the data you used.
if you are using jupyter notebook, the page will be opened in the output column. to open it in new tab, click the dtale loog and select ' 'open in new tab' 

## b. How to generate basic statistics and visualizations.
## c. How to explore relationships and patterns in the data.
## d. Any unique features or capabilities of each tool that you find noteworthy.

