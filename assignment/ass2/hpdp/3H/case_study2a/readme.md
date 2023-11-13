## Step 1: Selecting Automated EDA Tool: Autoviz

Autoviz is a powerful tool that allows users to easily visualize any dataset without the need for manual data manipulation or coding.

```
!pip install autoviz
```

## Step 2: Select a Malaysia dataset

The dataset can be downloaded from https://drive.google.com/file/d/1-6jBhXqAKTa3_2SUxo5lnhLcaMYD4Wkv/view The dataset is also uploaded to Github. In this project, we will link the dataset from Github.

### Overview Of The Dataset

The data are collected from an app called PriceCatcher which is a mobile app developed by the Ministry of Domestic Trade and Cost of Living (KPDN, formerly KPDNHEP) to help users compare the prices of key items in their area. Prices are collected and verified by groundstaff on a daily basis, with over 2 million prices collected every month. The dataset that we used are recorded from the year 2022/01 - 2023/10.

```
import numpy as np
import pandas as pd
from autoviz.AutoViz_Class import AutoViz_Class
```

```
from google.colab import drive
drive.mount ('/content/drive')
```

```
import zipfile
```

```
zip_file_path = '/content/drive/MyDrive/Colab Notebooks/Dataset/data.zip'
```

```
extraction_path = '/content/drive/MyDrive/Colab Notebooks/Dataset'
```

```
with zipfile.ZipFile(zip_file_path,'r') as zip_ref:
  zip_ref.extractall(extraction_path)
```

```
df = pd.read_csv('/content/drive/MyDrive/Colab Notebooks/Dataset/data.zip', compression = 'zip', index_col = 0)
```

```
df.head()
```

```
df.info()
```

```
df.isnull().sum(axis=0)
```

```
df.drop('address',axis='columns', inplace=True)
df.drop('premise',axis='columns', inplace=True)
df.head()
```

## Step 4: Implementation Of Automated EDA Tools
### a. Loading dataset into the tool
Autoviz have a function called “AutoViz_Class” that takes in a pandas DataFrame and generates visualizations. Here is an example of how to use it.

This will generate a variety of visualizations, including bar charts, line graphs, and scatter plots. These visualizations will be saved in the current working directory as HTML files that can be opened in a web browser for viewing.

```
AV = AutoViz_Class()
```

```
# AutoViz no displays plots automatically. You must perform %matplotlib inline just before you run AutoViz on your data.
%matplotlib inline
```

```
df = pd.DataFrame(df)
rows = df.shape[0]  
cols = df.shape[1] 
print(rows)
print(cols)
```

### b. Generate Basic Statistic & Visualization

This will generate a variety of visualizations, including bar charts, line graphs, and scatter plots. These visualizations will be saved in the current working directory as HTML files that can be opened in a web browser for viewing. In addition to generating visualizations, Autoviz also allows users to customize and refine their visualizations. For example, you can specify the types of visualizations you want to generate, as well as the color schemes and layouts of the charts.

Parameters:
*   filename: The name of the file containing the dataset.
*   sep: The delimiter used in the file.
*   depVar: The name of the target variable.
*   dfte: The dataframe containing the dataset.
* header: The row number of the header in the file.
* verbose: The level of verbosity. If it is 0 or 1, it only shows the plots on the notebook. If we give 2, it also saves the plots.
* lowess: A boolean indicating whether to use the LOWESS smoother for scatter plots.
* chart_format: The format of the generated charts. In this case, it is 'png'.
* max_rows_analyzed: The maximum number of rows to be analyzed from the dataset.
* max_cols_analyzed: The maximum number of columns to be analyzed from the dataset.

```
df = pd.DataFrame(df)
dft = AV.AutoViz(
    "",
    sep=",",
    depVar="",
    dfte=df,
    header=0,
    verbose=1,
    lowess=False,
    chart_format="svg",
    max_rows_analyzed=rows,
    max_cols_analyzed=cols,
    save_plot_dir=None
)
```
autoviz.png
autoviz_2.png
autoviz_3.png
autoviz_4.png

### c. Exploring relationships and patterns in the data

Based on the graph generated, we can see that:

minimum price is RM0.01 and the maximum price is RM170.00
Barangan segar has the highest normal distribution of the item group
Pasar Raya/Supermarket has the highest normal distribution of the premise type
Sayur-sayuran is the highest normal distribution of the item category
Susu bayi hold the maximum value of average price by item category
Minyak masak are the biggest word in workcloud for item.

## Step 5: Pros and Cons Analysis
| Aspect | Autoviz | Traditional |
|----------|----------|----------|
| Ease of Use	| Extremely user-friendly with minimal coding	| May have a steeper learning curve, requires coding proficiency |
| Automation	| Automates visualization selection	| Provides high customization options for tailored visualizations |
| Comprehensiveness	| Offers basic visualizations and statistics	| Allows advanced statistical and visual analyses beyond basics |
| Time-Saving	| Speeds up the initial data exploration	| Customization and in-depth analysis can be time-consuming |
| Customization	| Provides limited customization options	| Offers extensive customization for tailored, publication-quality visualizations |
| Advanced Analysis	| Limited for in-depth analysis	| Suitable for advanced statistical and visual analysis |
| Interactivity	| Static visualizations	| Some tools allow for interactive visualizations |
| Scalability	| Suitable for small to medium datasets	| Suitable for handling both small and large datasets |
| Learning Curve	| Minimal programming knowledge required	| May require significant programming skills |
| Data Transformation | Limited capabilities for complex transformations	| Allows complex data transformations and feature engineering |


---


Autoviz is a valuable tool for quick and automated data exploration, particularly for individuals who want an easy, code-light approach. It's useful for rapidly generating basic visualizations and getting an initial understanding of the data.

## Step 6: Conclusion
Insights:


1.   Baby goods recorded the highes average price compared to other item category.
2.   List item

3.   Baby goods recorded the highes average price compared to other item category.
4.   Some of the variables need to be cleaned before proceeding to a visualization process. For example, "item" column where the there is an issue with the data quality.
5.   Column "Item" need to be assessed as it has high cardinality that could impact data modelling.
6.   Most of the item prices in Negeri Sembilan are relatively higher than other states.
7.  In Malaysia, the most common premise type is Hypermarket.



---

Autoviz are exceptionally easy to use with minimal coding, making it ideal for beginners.Moreover it offers automation in visualization selection, saving time in initial data exploration. Next, provides a broad range of basic visualizations and summary statistics for a quick overview of the dataset.
It also offers some level of customization and is suitable for preliminary data exploration. However it have some cons which is imited for in-depth analysis; it's designed for quick, preliminary exploration. It also lacks advanced customization and interactivity options. Last but not least, it may not perform optimally for very large datasets.

My insight about Autoviz is that it is preferable when you need to quickly gain an initial understanding of your dataset or you have limited coding skills or want a point-and-click approach or time is a constraint, and you want to expedite preliminary data exploration or you have a moderately-sized dataset, not extremely large or complex.


## Step 7: References

[AutoViz github](https://github.com/AutoViML/AutoViz)
<br>
[Autoviz medium](https://medium.datadriveninvestor.com/autoviz-the-key-to-effortless-data-visualization-4b930b0c5ad9)
