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

* Calculate number of wins for White and Black respectively
```
result_counts = ddf['Result'].value_counts().compute()

white_wins_count = result_counts.get('1-0', 0)
black_wins_count = result_counts.get('0-1', 0)
```

* Calculate mean
```
mean_white_win = white_wins_count / num_rows
mean_black_win = black_wins_count / num_rows
```

* Calculate mean
```
mean_WElo = ddf['WhiteElo'].mean().compute()
mean_BElo = ddf['BlackElo'].mean().compute()
```

* Calculate mean
```
mean_Wrdiff = ddf['WhiteRatingDiff'].mean(skipna=True).compute()
mean_Brdiff = ddf['BlackRatingDiff'].mean(skipna=True).compute()
```

* Stats for all mean
```
print("White Wins Mean:", mean_white_win)
print("Black Wins Mean:", mean_black_win)
print("White's ELO Mean:", mean_WElo)
print("Black's ELO Mean:", mean_BElo)
print("White Rating Diff Mean:", mean_Wrdiff)
print("Black Rating Diff Mean:", mean_Brdiff)
```

* Calculate standard deviation of White and Black ELO
```
WElo_std = ddf['WhiteElo'].std().compute()
BElo_std = ddf['BlackElo'].std().compute()
```

* Display the standard deviation
```
print("White's ELO std deviation:", mean_WElo)
print("Black's ELO std deviation:", mean_BElo)
```

* Calculate how many Opening type were used
```
unique_values_counts = ddf['Opening'].value_counts().compute()

print("Unique Values and Counts:")
print(unique_values_counts)
```







## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.
[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

