# Assignment 2 - Case Study 2b - D-Tale
<a href="https://lux-api.readthedocs.io/en/latest/#"
target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

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

To explore the dataset, you can use the following tools and techniques:

- **Python Libraries**: Pandas, NumPy, and Matplotlib/Seaborn for data manipulation, exploration, and visualization.
- **Jupyter Notebooks**: To document analyses, visualize data, and share insights.
- **Statistical Methods**: Descriptive statistics, time series analysis, and regression modeling.
- **Geospatial Analysis**: If geographical data (such as state or district-level) is involved.

Additionally, machine learning techniques can be applied for predictive modeling or clustering if needed.

For more details, you can explore the official COVID-19 dataset repository maintained by MoH-Malaysia.

---

## Downloading the Dataset

**TODO** - add some explanation here
   

### Links of Dataset  
Cases by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/cases_state.csv  
Death by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/deaths_state.csv  
Vaccination by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_state.csv

> Instructions (delete this cell):
>
> - Load the dataset into a data frame using Pandas
> - Explore the number of rows & columns, ranges of values etc.
> - Handle missing, incorrect and invalid data
> - Perform any additional steps (parsing dates, creating additional columns, merging multiple dataset etc.) **bold text**

You can install the Python Package through PyPI


```python
!pip install dtale
```

    Requirement already satisfied: dtale in c:\users\user\anaconda3\lib\site-packages (3.7.0)
    Requirement already satisfied: dash-colorscales in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.0.4)
    Requirement already satisfied: dash-daq in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.5.0)
    Requirement already satisfied: Flask-Compress in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.14)
    Requirement already satisfied: future>=0.14.0 in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.18.3)
    Requirement already satisfied: kaleido in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.2.1)
    Requirement already satisfied: missingno in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.5.2)
    Requirement already satisfied: pandas in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.5.3)
    Requirement already satisfied: squarify in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.4.3)
    Requirement already satisfied: strsimpy in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.2.1)
    Requirement already satisfied: six in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.16.0)
    Requirement already satisfied: xlrd in c:\users\user\anaconda3\lib\site-packages (from dtale) (2.0.1)
    Requirement already satisfied: beautifulsoup4 in c:\users\user\anaconda3\lib\site-packages (from dtale) (4.12.2)
    Requirement already satisfied: certifi in c:\users\user\anaconda3\lib\site-packages (from dtale) (2023.7.22)
    Requirement already satisfied: flask-ngrok in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.0.25)
    Requirement already satisfied: lz4 in c:\users\user\anaconda3\lib\site-packages (from dtale) (4.3.2)
    Requirement already satisfied: cycler in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.11.0)
    Requirement already satisfied: dash-bootstrap-components<=1.3.1 in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.3.1)
    Requirement already satisfied: networkx in c:\users\user\anaconda3\lib\site-packages (from dtale) (3.1)
    Requirement already satisfied: scikit-learn in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.3.0)
    Requirement already satisfied: seaborn in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.12.2)
    Requirement already satisfied: statsmodels in c:\users\user\anaconda3\lib\site-packages (from dtale) (0.14.0)
    Requirement already satisfied: numpy in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.24.3)
    Requirement already satisfied: openpyxl!=3.2.0b1 in c:\users\user\anaconda3\lib\site-packages (from dtale) (3.0.10)
    Requirement already satisfied: xarray in c:\users\user\anaconda3\lib\site-packages (from dtale) (2023.6.0)
    Requirement already satisfied: dash in c:\users\user\anaconda3\lib\site-packages (from dtale) (2.14.1)
    Requirement already satisfied: et-xmlfile in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.1.0)
    Requirement already satisfied: plotly in c:\users\user\anaconda3\lib\site-packages (from dtale) (5.9.0)
    Requirement already satisfied: Flask<2.3 in c:\users\user\anaconda3\lib\site-packages (from dtale) (2.2.2)
    Requirement already satisfied: itsdangerous in c:\users\user\anaconda3\lib\site-packages (from dtale) (2.0.1)
    Requirement already satisfied: requests in c:\users\user\anaconda3\lib\site-packages (from dtale) (2.31.0)
    Requirement already satisfied: werkzeug<2.3 in c:\users\user\anaconda3\lib\site-packages (from dtale) (2.2.3)
    Requirement already satisfied: matplotlib in c:\users\user\anaconda3\lib\site-packages (from dtale) (3.7.2)
    Requirement already satisfied: scipy in c:\users\user\anaconda3\lib\site-packages (from dtale) (1.11.1)
    Requirement already satisfied: dash-html-components==2.0.0 in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (2.0.0)
    Requirement already satisfied: dash-core-components==2.0.0 in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (2.0.0)
    Requirement already satisfied: dash-table==5.0.0 in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (5.0.0)
    Requirement already satisfied: typing-extensions>=4.1.1 in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (4.7.1)
    Requirement already satisfied: retrying in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (1.3.4)
    Requirement already satisfied: ansi2html in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (1.8.0)
    Requirement already satisfied: nest-asyncio in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (1.5.6)
    Requirement already satisfied: setuptools in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (68.0.0)
    Requirement already satisfied: importlib-metadata in c:\users\user\anaconda3\lib\site-packages (from dash->dtale) (6.0.0)
    Requirement already satisfied: Jinja2>=3.0 in c:\users\user\anaconda3\lib\site-packages (from Flask<2.3->dtale) (3.1.2)
    Requirement already satisfied: click>=8.0 in c:\users\user\anaconda3\lib\site-packages (from Flask<2.3->dtale) (8.0.4)
    Requirement already satisfied: tenacity>=6.2.0 in c:\users\user\anaconda3\lib\site-packages (from plotly->dtale) (8.2.2)
    Requirement already satisfied: MarkupSafe>=2.1.1 in c:\users\user\anaconda3\lib\site-packages (from werkzeug<2.3->dtale) (2.1.1)
    Requirement already satisfied: soupsieve>1.2 in c:\users\user\anaconda3\lib\site-packages (from beautifulsoup4->dtale) (2.4)
    Requirement already satisfied: brotli in c:\users\user\anaconda3\lib\site-packages (from Flask-Compress->dtale) (1.1.0)
    Requirement already satisfied: contourpy>=1.0.1 in c:\users\user\anaconda3\lib\site-packages (from matplotlib->dtale) (1.0.5)
    Requirement already satisfied: fonttools>=4.22.0 in c:\users\user\anaconda3\lib\site-packages (from matplotlib->dtale) (4.25.0)
    Requirement already satisfied: kiwisolver>=1.0.1 in c:\users\user\anaconda3\lib\site-packages (from matplotlib->dtale) (1.4.4)
    Requirement already satisfied: packaging>=20.0 in c:\users\user\anaconda3\lib\site-packages (from matplotlib->dtale) (23.1)
    Requirement already satisfied: pillow>=6.2.0 in c:\users\user\anaconda3\lib\site-packages (from matplotlib->dtale) (9.4.0)
    Requirement already satisfied: pyparsing<3.1,>=2.3.1 in c:\users\user\anaconda3\lib\site-packages (from matplotlib->dtale) (3.0.9)
    Requirement already satisfied: python-dateutil>=2.7 in c:\users\user\anaconda3\lib\site-packages (from matplotlib->dtale) (2.8.2)
    Requirement already satisfied: pytz>=2020.1 in c:\users\user\anaconda3\lib\site-packages (from pandas->dtale) (2023.3.post1)
    Requirement already satisfied: charset-normalizer<4,>=2 in c:\users\user\anaconda3\lib\site-packages (from requests->dtale) (2.0.4)
    Requirement already satisfied: idna<4,>=2.5 in c:\users\user\anaconda3\lib\site-packages (from requests->dtale) (3.4)
    Requirement already satisfied: urllib3<3,>=1.21.1 in c:\users\user\anaconda3\lib\site-packages (from requests->dtale) (1.26.16)
    Requirement already satisfied: joblib>=1.1.1 in c:\users\user\anaconda3\lib\site-packages (from scikit-learn->dtale) (1.1.1)
    Requirement already satisfied: threadpoolctl>=2.0.0 in c:\users\user\anaconda3\lib\site-packages (from scikit-learn->dtale) (2.2.0)
    Requirement already satisfied: patsy>=0.5.2 in c:\users\user\anaconda3\lib\site-packages (from statsmodels->dtale) (0.5.3)
    Requirement already satisfied: colorama in c:\users\user\anaconda3\lib\site-packages (from click>=8.0->Flask<2.3->dtale) (0.4.6)
    Requirement already satisfied: zipp>=0.5 in c:\users\user\anaconda3\lib\site-packages (from importlib-metadata->dash->dtale) (3.11.0)
    


```python
import dtale
import pandas as pd
```


```python
cases = pd.read_csv(' https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/cases_state.csv') #Cases
death = pd.read_csv('https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/deaths_state.csv') #Death
vax = pd.read_csv('https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_state.csv')   #Vaccination
```


```python
cases
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>state</th>
      <th>cases_new</th>
      <th>cases_import</th>
      <th>cases_recovered</th>
      <th>cases_active</th>
      <th>cases_cluster</th>
      <th>cases_unvax</th>
      <th>cases_pvax</th>
      <th>cases_fvax</th>
      <th>...</th>
      <th>cases_0_4</th>
      <th>cases_5_11</th>
      <th>cases_12_17</th>
      <th>cases_18_29</th>
      <th>cases_30_39</th>
      <th>cases_40_49</th>
      <th>cases_50_59</th>
      <th>cases_60_69</th>
      <th>cases_70_79</th>
      <th>cases_80</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-01-25</td>
      <td>Johor</td>
      <td>4</td>
      <td>4</td>
      <td>0</td>
      <td>4</td>
      <td>0</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-01-25</td>
      <td>Kedah</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-01-25</td>
      <td>Kelantan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-01-25</td>
      <td>Melaka</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-01-25</td>
      <td>Negeri Sembilan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>22075</th>
      <td>2023-11-04</td>
      <td>Selangor</td>
      <td>89</td>
      <td>0</td>
      <td>256</td>
      <td>1074</td>
      <td>0</td>
      <td>10</td>
      <td>1</td>
      <td>10</td>
      <td>...</td>
      <td>2</td>
      <td>1</td>
      <td>4</td>
      <td>18</td>
      <td>27</td>
      <td>14</td>
      <td>9</td>
      <td>5</td>
      <td>3</td>
      <td>6</td>
    </tr>
    <tr>
      <th>22076</th>
      <td>2023-11-04</td>
      <td>Terengganu</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>337</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>22077</th>
      <td>2023-11-04</td>
      <td>W.P. Kuala Lumpur</td>
      <td>53</td>
      <td>0</td>
      <td>153</td>
      <td>1385</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>14</td>
      <td>18</td>
      <td>8</td>
      <td>4</td>
      <td>3</td>
      <td>3</td>
      <td>2</td>
    </tr>
    <tr>
      <th>22078</th>
      <td>2023-11-04</td>
      <td>W.P. Labuan</td>
      <td>1</td>
      <td>0</td>
      <td>4</td>
      <td>37</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>22079</th>
      <td>2023-11-04</td>
      <td>W.P. Putrajaya</td>
      <td>8</td>
      <td>0</td>
      <td>20</td>
      <td>326</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>22080 rows × 25 columns</p>
</div>




```python
death
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>state</th>
      <th>deaths_new</th>
      <th>deaths_bid</th>
      <th>deaths_new_dod</th>
      <th>deaths_bid_dod</th>
      <th>deaths_unvax</th>
      <th>deaths_pvax</th>
      <th>deaths_fvax</th>
      <th>deaths_boost</th>
      <th>deaths_tat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-03-17</td>
      <td>Johor</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-03-17</td>
      <td>Kedah</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-03-17</td>
      <td>Kelantan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-03-17</td>
      <td>Melaka</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-03-17</td>
      <td>Negeri Sembilan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21243</th>
      <td>2023-11-04</td>
      <td>Selangor</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21244</th>
      <td>2023-11-04</td>
      <td>Terengganu</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21245</th>
      <td>2023-11-04</td>
      <td>W.P. Kuala Lumpur</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21246</th>
      <td>2023-11-04</td>
      <td>W.P. Labuan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21247</th>
      <td>2023-11-04</td>
      <td>W.P. Putrajaya</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>21248 rows × 11 columns</p>
</div>




```python
vax
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>state</th>
      <th>daily_partial</th>
      <th>daily_full</th>
      <th>daily_booster</th>
      <th>daily_booster2</th>
      <th>daily</th>
      <th>daily_partial_adol</th>
      <th>daily_full_adol</th>
      <th>daily_booster_adol</th>
      <th>...</th>
      <th>sinopharm2</th>
      <th>sinopharm3</th>
      <th>sinopharm4</th>
      <th>cansino</th>
      <th>cansino3</th>
      <th>cansino4</th>
      <th>pending1</th>
      <th>pending2</th>
      <th>pending3</th>
      <th>pending4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-02-24</td>
      <td>Johor</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021-02-24</td>
      <td>Kedah</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021-02-24</td>
      <td>Kelantan</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-02-24</td>
      <td>Melaka</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021-02-24</td>
      <td>Negeri Sembilan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>15835</th>
      <td>2023-11-10</td>
      <td>Selangor</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15836</th>
      <td>2023-11-10</td>
      <td>Terengganu</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15837</th>
      <td>2023-11-10</td>
      <td>W.P. Kuala Lumpur</td>
      <td>0</td>
      <td>0</td>
      <td>4</td>
      <td>4</td>
      <td>8</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15838</th>
      <td>2023-11-10</td>
      <td>W.P. Labuan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15839</th>
      <td>2023-11-10</td>
      <td>W.P. Putrajaya</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>15840 rows × 51 columns</p>
</div>


Inner Join

```python
df = cases.merge(death,on=['date','state']).merge(vax,on=['date','state'])
df_row, df_cols = df.shape
```


```python
print(f'Total Columns: {df_cols}')
```

    Total Columns: 83
    


```python
df.set_index('date', inplace=True)
```


```python
df.index = pd.to_datetime(df.index.get_level_values(0))
```


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 15744 entries, 2021-02-24 to 2023-11-04
    Data columns (total 82 columns):
     #   Column                Non-Null Count  Dtype 
    ---  ------                --------------  ----- 
     0   state                 15744 non-null  object
     1   cases_new             15744 non-null  int64 
     2   cases_import          15744 non-null  int64 
     3   cases_recovered       15744 non-null  int64 
     4   cases_active          15744 non-null  int64 
     5   cases_cluster         15744 non-null  int64 
     6   cases_unvax           15744 non-null  int64 
     7   cases_pvax            15744 non-null  int64 
     8   cases_fvax            15744 non-null  int64 
     9   cases_boost           15744 non-null  int64 
     10  cases_child           15744 non-null  int64 
     11  cases_adolescent      15744 non-null  int64 
     12  cases_adult           15744 non-null  int64 
     13  cases_elderly         15744 non-null  int64 
     14  cases_0_4             15744 non-null  int64 
     15  cases_5_11            15744 non-null  int64 
     16  cases_12_17           15744 non-null  int64 
     17  cases_18_29           15744 non-null  int64 
     18  cases_30_39           15744 non-null  int64 
     19  cases_40_49           15744 non-null  int64 
     20  cases_50_59           15744 non-null  int64 
     21  cases_60_69           15744 non-null  int64 
     22  cases_70_79           15744 non-null  int64 
     23  cases_80              15744 non-null  int64 
     24  deaths_new            15744 non-null  int64 
     25  deaths_bid            15744 non-null  int64 
     26  deaths_new_dod        15744 non-null  int64 
     27  deaths_bid_dod        15744 non-null  int64 
     28  deaths_unvax          15744 non-null  int64 
     29  deaths_pvax           15744 non-null  int64 
     30  deaths_fvax           15744 non-null  int64 
     31  deaths_boost          15744 non-null  int64 
     32  deaths_tat            15744 non-null  int64 
     33  daily_partial         15744 non-null  int64 
     34  daily_full            15744 non-null  int64 
     35  daily_booster         15744 non-null  int64 
     36  daily_booster2        15744 non-null  int64 
     37  daily                 15744 non-null  int64 
     38  daily_partial_adol    15744 non-null  int64 
     39  daily_full_adol       15744 non-null  int64 
     40  daily_booster_adol    15744 non-null  int64 
     41  daily_booster2_adol   15744 non-null  int64 
     42  daily_partial_child   15744 non-null  int64 
     43  daily_full_child      15744 non-null  int64 
     44  daily_booster_child   15744 non-null  int64 
     45  daily_booster2_child  15744 non-null  int64 
     46  cumul_partial         15744 non-null  int64 
     47  cumul_full            15744 non-null  int64 
     48  cumul_booster         15744 non-null  int64 
     49  cumul_booster2        15744 non-null  int64 
     50  cumul                 15744 non-null  int64 
     51  cumul_partial_adol    15744 non-null  int64 
     52  cumul_full_adol       15744 non-null  int64 
     53  cumul_booster_adol    15744 non-null  int64 
     54  cumul_booster2_adol   15744 non-null  int64 
     55  cumul_partial_child   15744 non-null  int64 
     56  cumul_full_child      15744 non-null  int64 
     57  cumul_booster_child   15744 non-null  int64 
     58  cumul_booster2_child  15744 non-null  int64 
     59  pfizer1               15744 non-null  int64 
     60  pfizer2               15744 non-null  int64 
     61  pfizer3               15744 non-null  int64 
     62  pfizer4               15744 non-null  int64 
     63  sinovac1              15744 non-null  int64 
     64  sinovac2              15744 non-null  int64 
     65  sinovac3              15744 non-null  int64 
     66  sinovac4              15744 non-null  int64 
     67  astra1                15744 non-null  int64 
     68  astra2                15744 non-null  int64 
     69  astra3                15744 non-null  int64 
     70  astra4                15744 non-null  int64 
     71  sinopharm1            15744 non-null  int64 
     72  sinopharm2            15744 non-null  int64 
     73  sinopharm3            15744 non-null  int64 
     74  sinopharm4            15744 non-null  int64 
     75  cansino               15744 non-null  int64 
     76  cansino3              15744 non-null  int64 
     77  cansino4              15744 non-null  int64 
     78  pending1              15744 non-null  int64 
     79  pending2              15744 non-null  int64 
     80  pending3              15744 non-null  int64 
     81  pending4              15744 non-null  int64 
    dtypes: int64(81), object(1)
    memory usage: 10.0+ MB
    


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>state</th>
      <th>cases_new</th>
      <th>cases_import</th>
      <th>cases_recovered</th>
      <th>cases_active</th>
      <th>cases_cluster</th>
      <th>cases_unvax</th>
      <th>cases_pvax</th>
      <th>cases_fvax</th>
      <th>cases_boost</th>
      <th>...</th>
      <th>sinopharm2</th>
      <th>sinopharm3</th>
      <th>sinopharm4</th>
      <th>cansino</th>
      <th>cansino3</th>
      <th>cansino4</th>
      <th>pending1</th>
      <th>pending2</th>
      <th>pending3</th>
      <th>pending4</th>
    </tr>
    <tr>
      <th>date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-02-24</th>
      <td>Johor</td>
      <td>318</td>
      <td>0</td>
      <td>518</td>
      <td>6165</td>
      <td>189</td>
      <td>318</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2021-02-24</th>
      <td>Kedah</td>
      <td>17</td>
      <td>0</td>
      <td>187</td>
      <td>579</td>
      <td>4</td>
      <td>17</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2021-02-24</th>
      <td>Kelantan</td>
      <td>53</td>
      <td>0</td>
      <td>100</td>
      <td>698</td>
      <td>26</td>
      <td>53</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2021-02-24</th>
      <td>Melaka</td>
      <td>26</td>
      <td>0</td>
      <td>37</td>
      <td>365</td>
      <td>21</td>
      <td>26</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2021-02-24</th>
      <td>Negeri Sembilan</td>
      <td>1392</td>
      <td>0</td>
      <td>119</td>
      <td>2210</td>
      <td>1358</td>
      <td>1392</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2023-11-04</th>
      <td>Selangor</td>
      <td>89</td>
      <td>0</td>
      <td>256</td>
      <td>1074</td>
      <td>0</td>
      <td>10</td>
      <td>1</td>
      <td>10</td>
      <td>68</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2023-11-04</th>
      <td>Terengganu</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>337</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2023-11-04</th>
      <td>W.P. Kuala Lumpur</td>
      <td>53</td>
      <td>0</td>
      <td>153</td>
      <td>1385</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
      <td>48</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2023-11-04</th>
      <td>W.P. Labuan</td>
      <td>1</td>
      <td>0</td>
      <td>4</td>
      <td>37</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2023-11-04</th>
      <td>W.P. Putrajaya</td>
      <td>8</td>
      <td>0</td>
      <td>20</td>
      <td>326</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>4</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>15744 rows × 82 columns</p>
</div>




```python
d = dtale.show(df)
```


```python
d
```



<iframe
    width="100%"
    height="475"
    src="http://Admin:40000/dtale/iframe/5"
    frameborder="0"
    allowfullscreen

></iframe>






    



    2023-11-12 01:25:08,543 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,567 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,570 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,573 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,577 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,580 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,600 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,603 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,606 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,609 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,612 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,618 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,623 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,625 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,628 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,630 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,634 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,641 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,644 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,647 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,650 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,653 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,660 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,662 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,665 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,669 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,671 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,675 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,693 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,697 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,699 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,702 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,706 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,708 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,712 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,715 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,721 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,725 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,727 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,732 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,735 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,738 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,741 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,748 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,754 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,758 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,763 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,765 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,769 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,775 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,778 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,782 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,785 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,789 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,792 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,796 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,798 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,819 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,822 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,827 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,830 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,833 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,835 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,838 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,846 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,848 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,851 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,854 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,856 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,859 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,861 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,863 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,865 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,873 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,877 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,880 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,883 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,886 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,888 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,891 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,893 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,899 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,904 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,909 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,912 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,917 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,920 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,923 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,937 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,948 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,952 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,955 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,959 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,964 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,971 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,975 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,979 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,983 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,987 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,990 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:08,998 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,001 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,005 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,009 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,014 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,021 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,025 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,027 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,032 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,037 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,042 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,060 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,063 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,067 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,075 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,080 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,082 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,090 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,095 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,097 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,104 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,109 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,113 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,133 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,138 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,141 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,146 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,150 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,155 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,158 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,166 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,169 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,173 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,178 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,183 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,187 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,191 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,199 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,204 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,208 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,212 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,215 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,219 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,222 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,225 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,232 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,236 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,239 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,243 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,247 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,250 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,253 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,257 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,262 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,281 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,285 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,289 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,292 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,297 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,299 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,303 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,305 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,312 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,381 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,386 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,391 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,394 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,402 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,406 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,411 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,415 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,419 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,423 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,426 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,432 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,439 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,444 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,447 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,451 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,456 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,460 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,465 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,479 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,489 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,493 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,497 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,502 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,506 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,509 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,514 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,517 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,526 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,530 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,533 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,539 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,543 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,547 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,552 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,556 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,564 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,568 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,572 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,577 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,582 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,587 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,591 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,600 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,605 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,610 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,614 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,618 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,623 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,635 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,646 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,651 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,655 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,660 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,664 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,670 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,678 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,684 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,688 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,692 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,696 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,699 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,707 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,711 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,715 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,719 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,723 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,726 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,729 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,737 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,742 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,746 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,749 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,753 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,758 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,775 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,783 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,787 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,791 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,795 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,799 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,890 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,893 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,896 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,898 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,901 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,903 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,906 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,908 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,911 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,914 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,919 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,927 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,930 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,933 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,937 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,940 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,944 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:09,947 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,190 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,196 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,199 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,202 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,205 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,208 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,211 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,214 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,216 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,219 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,226 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,229 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,232 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,235 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,238 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,241 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,245 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,248 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,251 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,269 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,273 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,275 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,279 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,282 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,285 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,289 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,291 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,295 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,302 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,305 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,309 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,311 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,314 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,317 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,321 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,326 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,330 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,333 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,336 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,339 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,343 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,347 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,350 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,356 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,360 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,362 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,367 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,371 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,374 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,377 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,397 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,400 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,404 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,407 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,411 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,415 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,423 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,427 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,431 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,434 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,437 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,440 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,445 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,449 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,453 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,456 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,458 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,461 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,465 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,467 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,474 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,477 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,480 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,483 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,486 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,489 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,491 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,498 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,514 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,517 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,519 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,523 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,527 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,530 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,539 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,543 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,548 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,552 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,556 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,565 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,569 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,572 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,577 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,582 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,589 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,593 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,598 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,602 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,623 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,627 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,632 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,635 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,639 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,646 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,651 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,655 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,659 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,663 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,671 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,676 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,680 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,684 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,688 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,696 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,700 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,705 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,708 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,713 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,733 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,737 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,740 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,745 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,752 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,759 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,762 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,767 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,771 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,781 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,784 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,787 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,792 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,796 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,803 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,808 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,812 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,816 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,837 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,841 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,845 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,850 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,858 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,861 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,865 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,867 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,871 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,878 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,882 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,886 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,889 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,893 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,896 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,905 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,908 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,912 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,915 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,936 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,941 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,944 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,949 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,952 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,960 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,965 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:10,969 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,035 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,043 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,047 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,051 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,055 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,060 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,067 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,070 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,075 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,079 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,083 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,103 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,106 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,110 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,113 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,117 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,121 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,124 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,132 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,136 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,139 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,143 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,146 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,150 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,157 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,160 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,164 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,169 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,172 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,177 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,183 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,187 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,191 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,195 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,200 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,219 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,223 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,227 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,231 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,235 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,244 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,248 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,252 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,256 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,260 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,269 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,273 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,276 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,280 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,288 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,290 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,295 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,297 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,302 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,314 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,326 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,330 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,334 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,341 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,344 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,348 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,351 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,357 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,361 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,364 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,367 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,376 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,379 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,383 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,386 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,401 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,408 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,412 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,416 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,420 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,422 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,425 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,430 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,435 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,439 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,443 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,483 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,491 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,505 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,508 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,510 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,513 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,520 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,522 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,524 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,527 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,529 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,531 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,534 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,538 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,555 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,559 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,563 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,565 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,568 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:25:11,571 - WARNING  - findfont: Font family 'Heiti TC' not found.
    2023-11-12 01:36:14,372 - ERROR    - Exception occurred while processing request: It appears there is duplicates in your index, please specify an aggregation!
    Traceback (most recent call last):
      File "C:\Users\User\anaconda3\Lib\site-packages\dtale\views.py", line 119, in _handle_exceptions
        return func(*args, **kwargs)
               ^^^^^^^^^^^^^^^^^^^^^
      File "C:\Users\User\anaconda3\Lib\site-packages\dtale\views.py", line 4278, in get_timeseries_analysis
        data = ts_rpt.run()
               ^^^^^^^^^^^^
      File "C:\Users\User\anaconda3\Lib\site-packages\dtale\timeseries_analysis.py", line 48, in run
        return self.report.run(data)
               ^^^^^^^^^^^^^^^^^^^^^
      File "C:\Users\User\anaconda3\Lib\site-packages\dtale\timeseries_analysis.py", line 93, in run
        df = build_data(data, self.cfg)
             ^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "C:\Users\User\anaconda3\Lib\site-packages\dtale\timeseries_analysis.py", line 18, in build_data
        raise ValueError(
    ValueError: It appears there is duplicates in your index, please specify an aggregation!
    

![D-Tale1.png](attachment:D-Tale1.png)

The image above shows the D-Tale menu to perform analysis.

Next, go to "Describe" to see the details for every columns.

Once you click on the "Describe", a new tab will open and shows the details for each column.

![D-Tale2.png](attachment:D-Tale2.png)

Next, to generate statistics and visualization, go to "Charts". 

Then, a new tab will appear and shows the menu of charts creation according to your preference.

![D-Tale3.png](attachment:D-Tale3.png)

For example, we want to see line chart for sum of 'cases_new' over time by month. So, we need to choose date(Monthly) for our x-axis and cases_new for our y-axis and choose sum for our aggregation. Then, the charts will be generated automatically.

![D-Tale4.png](attachment:D-Tale4.png)

Next, to see the correlations between all the columns, we can select "Correlation" in the menu. Once we click on the "Correlations", a new tab that counts the correlations will be generated automatically as shown in the image below.

![D-Tale5.png](attachment:D-Tale5.png)

If we want to see the trend of the 'death_new' over time, we can go to "Time Series Analysis".

Image below shows the generated graph of 'death_new' over time.

![D-Tale6.png](attachment:D-Tale6.png)


```python

```
