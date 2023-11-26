<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Assignment 3: Exploratory Data Analysis using Big Data

## Your profile
Group Name : <b>BERUK</b>

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
| HAFIZULSHAH BIN SHAROM | A21EC0027 |Assignment 3 - 100% Contribution| 
| MUHAMMAD HASAN BIN CHE ABDULLAH | A21EC0077 |Assignment 4|
| ABDUL MUHAIMIN BIN ABDUL RAZAK | A21EC0002 |Assignment 5|  
| MUHAMMAD HAZIM BIN SALMAN | A21EC0078 |Assignment 5|

## Objective
The objective of this assignment is to perform Exploratory Data Analysis (EDA) on a large dataset using big data tools and techniques. EDA is a critical step in understanding the characteristics of a dataset and uncovering insights that can inform further analysis and decision-making.

### 1. Data Selection

#### Chess Games Statistics
#### Context
Chess is one of the more famous board games of the world and one of the most studied. With it's more than 4 GB of information this can be a good opportunity to work with a huge dataset and practice on how to handle it.

#### Content
This dataset contains 6.25 Million chess games played on lichess.org during July of 2016.
Some of the games have Stockfish analysis evaluations like* [%eval 2.35] (235 centipawn advantage)* always from White's point of view. These are evaluations of the movement made by a player. <br><br>

| Event | Game type |
| --- | --- |
| White | White's ID. |
| Black | Black's ID. |
| Result | Game Result (1-0 White wins) (0-1 Black wins) |
| UTCDate | UTC Date. |
| UTCTime | UTC Time. |
| WhiteElo | White's ELO. |
| BlackElo | Black's ELO. |
| WhiteRatingDiff | White's rating points |difference after the game. |
| BlackRatingDiff | Blacks's rating points |difference after the game. |
| ECO | Opening in ECO encoding. |
| Opening | Opening name. |
| TimeControl | Time of the game for each player in seconds. The number after the increment is the number of seconds before the player's clock starts ticking in each turn. |
| Termination | Reason of the game's end. |
| AN | Movements in Movetext format. |

### 2. Data Acquisition
Link : [Chess Games](https://www.kaggle.com/datasets/arevel/chess-games?select=chess_games.csv)

The step to acquire the dataset consist of 2 major steps ;

Step 1 : Upload account API (Kaggle.json) from Kaggle

```
from google.colab import files
files.upload()
```
```
!rm -r ~/.kaggle
!mkdir ~/.kaggle
!mv ./kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

![image](https://github.com/drshahizan/Python_EDA/assets/146704678/0a56370b-5440-4dc6-b670-10349a394a6d)<br>
The API token can be obtained from Account → Settings → API → Create New Token
<br><br><br>
Step 2 : Download and extract the dataset

```
!kaggle datasets download -d arevel/chess-games
```

![image](https://github.com/drshahizan/Python_EDA/assets/146704678/d8d20d8c-f972-4e93-a02b-ae155bf3723f)<br>
The download command get be obtained by clicking on the three dots at the top right corner of the page → Copy API command
<br><br>
Unpack ZIP folder
```
import zipfile
zip_ref = zipfile.ZipFile('/content/chess-games.zip', 'r')
zip_ref.extractall('/content')
zip_ref.close()
```

### 3. Setting Up the Environment
* Install Dask to use its library
```
!pip install dask
```
We are using Dask dataframe sincce Dask can handle large datasets better than Pandas
<br>

* Import necessary libraries
```
import dask.dataframe as dd
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import gc
```
<br>

* Read CSV using Dask to reate Dask Dataframe
```
ddf = dd.read_csv('/content/chess_games.csv')
```
<br>

*Print data types and head (5 first rows) to check the dataframe
```
print(ddf.dtypes)
```
```
print(ddf.dtypes)
```

### 4. Data Preprocessing
* Check for missing values
```
missing_values = ddf.isnull().sum().compute()
print(missing_values)
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/38d5128f-6ddc-40b1-9297-afc3b91c98ab) <br>
<br>

* Drop rows with missing values
```
ddf = ddf.dropna()
```
We drop these rows since Null ells can cause incorrectness when doing calulations and generating graph

* Re-check for null / missing value
```
missing_values = ddf.isnull().sum().compute()
print(missing_values)
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/a17b1a63-7e4b-4e9c-8dd1-04c848c7147f) <br>
<br>

* Optimizing dataframe by getting rid of 'int64' and 'float64'
* This step is to reduce the memory usage of the dataframe
```
for col in ddf.columns:
    col_type = ddf[col].dtype

    # Ignore Column type 'Object'
    if col_type != 'object':
        c_min = ddf[col].min().compute()
        c_max = ddf[col].max().compute()
        # Downcast Integer Type
        if str(col_type)[:3] == 'int':
            if c_min > np.iinfo(np.int8).min and c_max < np.iinfo(np.int8).max:
                ddf[col] = ddf[col].astype(np.int8)
            elif c_min > np.iinfo(np.int16).min and c_max < np.iinfo(np.int16).max:
                ddf[col] = ddf[col].astype(np.int16)
            elif c_min > np.iinfo(np.int32).min and c_max < np.iinfo(np.int32).max:
                ddf[col] = ddf[col].astype(np.int32)
            elif c_min > np.iinfo(np.int64).min and c_max < np.iinfo(np.int64).max:
                ddf[col] = ddf[col].astype(np.int64)
        # Downcast Float Type
        else:
            if c_min > np.finfo(np.float16).min and c_max < np.finfo(np.float16).max:
                ddf[col] = ddf[col].astype(np.float16)
            elif c_min > np.finfo(np.float32).min and c_max < np.finfo(np.float32).max:
                ddf[col] = ddf[col].astype(np.float32)
            else:
                ddf[col] = ddf[col].astype(np.float64)
```
<br>

* Change the datatype of UTCDate from type 'Object' into 'Datetime'
```
ddf['UTCDate'] = dd.to_datetime(ddf['UTCDate'], format='%Y.%m.%d', errors='coerce')
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/57345254-b9c2-4af4-927c-2f7df7b4d116) <br>
<br>

### 5. Exploratory Data Analysis
#### a. Summary Statistics: Compute basic statistics such as mean, median, standard deviation, and quantiles for relevant numerical variables

* Calculate number of rows in the dataframe
```
num_rows = ddf.shape[0].compute()
print("Number of Rows:", num_rows)
```
<br>

* Calculate number of wins for White and Black respectively
```
result_counts = ddf['Result'].value_counts().compute()

white_wins_count = result_counts.get('1-0', 0)
black_wins_count = result_counts.get('0-1', 0)
```
<br>

* Calculate mean
```
mean_white_win = white_wins_count / num_rows
mean_black_win = black_wins_count / num_rows
```
<br>

* Calculate mean
```
mean_WElo = ddf['WhiteElo'].mean().compute()
mean_BElo = ddf['BlackElo'].mean().compute()
```
<br>

* Calculate mean
```
mean_Wrdiff = ddf['WhiteRatingDiff'].mean(skipna=True).compute()
mean_Brdiff = ddf['BlackRatingDiff'].mean(skipna=True).compute()
```
<br>

* Stats for all mean
```
print("White Wins Mean:", mean_white_win)
print("Black Wins Mean:", mean_black_win)
print("White's ELO Mean:", mean_WElo)
print("Black's ELO Mean:", mean_BElo)
print("White Rating Diff Mean:", mean_Wrdiff)
print("Black Rating Diff Mean:", mean_Brdiff)
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/7ab3fc6a-f55b-4484-ba69-705816a08f05) <br>
<br>

* Calculate standard deviation of White and Black ELO
```
WElo_std = ddf['WhiteElo'].std().compute()
BElo_std = ddf['BlackElo'].std().compute()
```
<br>

* Display the standard deviation
```
print("White's ELO std deviation:", mean_WElo)
print("Black's ELO std deviation:", mean_BElo)
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/0a6746af-5c8c-4349-8fca-1a723c1a3960) <br>
<br>

* Calculate how many Opening type were used
```
unique_values_counts = ddf['Opening'].value_counts().compute()

print("Unique Values and Counts:")
print(unique_values_counts)
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/64d1b9e4-ed63-45eb-9bc5-a044c5aebbe4) <br>
<br>

#### b. Data Visualization: Create visualizations like histograms, box plots, scatter plots, and heatmaps to understand data distributions, correlations, and outliers

* Histogram of White Elo using Seaborn
```
plt.figure(figsize=(12, 6))

sns.histplot(ddf['WhiteElo'], bins=20, kde=True, color='green')

plt.xlabel('White ELO')
plt.ylabel('Frequency')

plt.title('Distribution of White Elo')
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/1df84d1f-0177-4700-bd18-511434447b23) <br>
<br>

* Histogram of Black Elo using Seaborn
```
plt.figure(figsize=(12, 6))

sns.histplot(ddf['BlackElo'], bins=20, kde=True, color='blue')

plt.xlabel('Black ELO')
plt.ylabel('Frequency')

plt.title('Distribution of Black Elo')
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/c9801801-fee5-41c5-9863-2c38430d0258) <br>
<br>

* Bar plot of game results
```
plt.figure(figsize=(12, 6))

df_for_plot = ddf.compute()

sns.barplot(x=df_for_plot['Result'].value_counts().index, y=df_for_plot['Result'].value_counts())
plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/f8eb91eb-47c8-4425-a09a-f2e72c515903) <br>
<br>

* Releasing memory by deleting unused variables
```
del df_for_plot

gc.collect()
```
<br>

* Scatter plot of Opening moves used
```
plt.figure(figsize=(16, 6))

scatter_column = 'Opening'

df_for_plot = ddf[scatter_column].compute()
value_counts = df_for_plot.value_counts()

top_10_moves = value_counts.head(10)

plt.scatter(x=top_10_moves.index, y=top_10_moves.values)
plt.xlabel(scatter_column)
plt.ylabel('Frequency')
plt.title(f'Scatter Plot of Top 25 {scatter_column} Frequencies')
plt.xticks(rotation=45)  # Rotate x-axis labels for better visibility
plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/03a237cd-9fbf-4d90-a6b2-2aa65323ba25) <br>
<br>

* Releasing memory by deleting unused variables
```
del df_for_plot
del value_counts
del top_10_moves
del BElo_std
del WElo_std
del black_wins_count
del white_wins_count
del c_max
del c_min
del col
del col_type
del mean_BElo
del mean_Brdiff
del mean_WElo
del mean_Wrdiff
del mean_black_win
del mean_white_win
del unique_values_counts

gc.collect()
```
<br>

#### c. Data Exploration: Explore the dataset's structure and identify any patterns, trends, or anomalies. Pay attention to variables' distributions, relationships, and potential insights

* Finding the most used Opening
```
plt.figure(figsize=(12, 6))

opening_count = ddf['Opening'].value_counts().compute()

top_5_openings = opening_count.head(5)

top_5_openings.plot(kind='bar')

plt.xlabel('Opening')
plt.ylabel('Counts')
plt.title('Top 5 Most Common Opening')
plt.xticks(rotation=45)

plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/3ae96469-906a-4e50-b810-b5caa6fea867) <br>
Here we can see that the top 5 most commonly used opening are:
1. Van't Kruijs Opening
2. Scandinavian Defense: Mieses-Kotroc Variation
3. Modern Defense
4. Horwitz Defense
5. Sicilian Defense
<br>

* Plot histograms for numerical columns
```
numerical_columns = ['WhiteElo', 'BlackElo', 'WhiteRatingDiff', 'BlackRatingDiff']
ddf[numerical_columns].compute().hist(bins=20, figsize=(12, 8))
plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/76273c58-a4c6-4838-9268-9dcdbb262343) <br>
Here we can see that most player's ELO are in the range of around 1500 to 2000
<br>

* Explore relationships between Elo ratings
```
sns.pairplot(ddf.compute(), vars=['WhiteElo', 'BlackElo', 'WhiteRatingDiff', 'BlackRatingDiff'])
plt.figure(figsize=(12, 6))

plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/8e220221-39b3-4f6d-8c35-18d2c5d16fcb) <br>
<br>

* Explore the distribution of results
```
sns.countplot(data=ddf.compute(), x='Result')
plt.figure(figsize=(12, 6))

plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/ee263042-643b-452a-896c-a0d3cf294df8) <br>
Here we can see that the winrate of White is slightly higher than black. So, the chancce of winning when playing White is more favorable
<br>

* Explore trends over time
```
ddf.groupby('UTCDate').size().compute().plot(figsize=(12, 6))
plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/3e6c0a86-928d-4263-9ae1-c6a665dd4311) <br>
<br>

* Explore the distribution of the 'Event' column
```
plt.figure(figsize=(12, 6))

sns.countplot(data=ddf.compute(), x='Event')
plt.xticks(rotation=90)
plt.show()
```
![image](https://github.com/drshahizan/Python_EDA/assets/146704678/0a7468d8-33ec-432c-a7c6-0ccd8613dc60) <br>
Here we can see that most player are playing the Blitz event and least player play Correspondence event
<br>

#### d. Feature Engineering: If applicable, create new features or transform existing ones to better support your analysis

* Create a new feature representing the average Elo rating of the players in each game
```
ddf['AvgElo'] = (ddf['WhiteElo'] + ddf['BlackElo']) / 2
```
This new column is created to show new data which is the average ELO of the match
<br>

* Create a new feature representing the count of moves in each game
```
ddf['MoveCount'] = ddf['AN'].str.split().apply(len, meta=('AN', 'int'))
```
This new column is created to show how many moves it takes for the math to end to summarize the AN column


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.
[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

