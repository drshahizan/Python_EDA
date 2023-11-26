**Name: NG SUANG JOO**

**Matric Number: A21EC0102**

**Date: 19/11/2023**

#**Dataset: New York Bus Rides Service**
Company offers rides on fixed routes (defined count and location of stations) at different tmes of the day. The customer books any one of these rides based on their needs (travel time, distance, price etc.). We are constantly trying to improve our offerings from a product, operations, growth side to improve our conversion through a very data driven approach.

The customer lands on the home screen and then starts a search by entering a pickup and drop off location. The last step is when they click on the book button on the check-out page.

##**Dataset**
* **Search**

This file represents all the searches made on the platform for booking

1. session_id: Session of the search
2. search_id: Unique search in the session
3. user_id: ID of the user
4. search_city: City where the search happened
5. search_time: Local time of the search
6. num_of_results: Number of results returned for the search
7. is_result: Whether a search gave a result or not
8. median_pickup_walk_time: Estimated time taken by user to walk from his desired pickup to the bus station
9. median_dropoff_walk_time: Estimated time taken by user to walk from the bus station his desired destination
10. median_bus_travel_time: Estimated bus travel time
11. high_demand_val: Indicates very few seats left or that the bus is full
12. user_device_os: Platform of the mobile device
13. user_device_app_version: App version number



##**Loading the Dataset**


```python
from google.colab import drive
drive.mount('/content/drive')
```

    Drive already mounted at /content/drive; to attempt to forcibly remount, call drive.mount("/content/drive", force_remount=True).



```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import random

%matplotlib inline

```

##**Sampling**
Random sample of 10% of dataset


```python
file = '/content/drive/My Drive/Datasets/newyorkbus/searches.csv'
n = sum(1 for line in open(file))-1
s = n//10
skip = sorted(random.sample(range(1, n+1), n-s))
df = pd.read_csv(file, skiprows=skip)
df.head()
```





  <div id="df-6ad45028-c7f2-4aa7-a6e4-31bfb5cad012" class="colab-df-container">
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
      <th>session_id</th>
      <th>search_id</th>
      <th>user_id</th>
      <th>search_city</th>
      <th>search_time</th>
      <th>num_of_results</th>
      <th>is_result</th>
      <th>median_pickup_walk_time</th>
      <th>median_dropoff_walk_time</th>
      <th>median_bus_travel_time</th>
      <th>high_demand_val</th>
      <th>user_device_os</th>
      <th>user_device_app_version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>911ab421-5800-401f-8045-4427c51cc351</td>
      <td>375890ed-3e8b-400f-b40b-bab770022e5b</td>
      <td>5d6d32ebf321e600193e3d39</td>
      <td>New York</td>
      <td>2020-02-16 13:47:25.811 UTC</td>
      <td>10</td>
      <td>True</td>
      <td>1020.0</td>
      <td>1680.0</td>
      <td>3673.0</td>
      <td>0</td>
      <td>ios</td>
      <td>3390.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ce7a234f-ddeb-4de0-844f-bcfd194ca1f5</td>
      <td>aa82ffda-c53e-4e48-a39f-87c4df5d102c</td>
      <td>5d8073b18743200019da237c</td>
      <td>New York</td>
      <td>2019-12-10 19:49:25.792 UTC</td>
      <td>40</td>
      <td>True</td>
      <td>300.0</td>
      <td>1860.0</td>
      <td>1418.0</td>
      <td>0</td>
      <td>android</td>
      <td>286.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8bd1472e-404a-489f-a8aa-c4633d51929a</td>
      <td>6ee93693-ff10-49d0-8f38-cc89ac6f0b18</td>
      <td>59ddadd78f279c000f6e15b0</td>
      <td>New York</td>
      <td>2020-02-23 16:26:56.543 UTC</td>
      <td>10</td>
      <td>True</td>
      <td>1080.0</td>
      <td>1380.0</td>
      <td>4376.5</td>
      <td>0</td>
      <td>ios</td>
      <td>3390.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>711c199e-23e7-450a-8482-ee36b78bf291</td>
      <td>6ea972a3-28d9-4bb6-9100-4acfba900af5</td>
      <td>5ce898dfbcc3ed001a3de358</td>
      <td>New York</td>
      <td>2019-12-05 07:55:20.539 UTC</td>
      <td>10</td>
      <td>True</td>
      <td>480.0</td>
      <td>480.0</td>
      <td>3939.5</td>
      <td>0</td>
      <td>android</td>
      <td>284.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3f2ea46a-a082-4eeb-9722-003e1461a10c</td>
      <td>2ee71414-2596-43f8-b67d-0d2846d953bb</td>
      <td>5ca5e5a87c646d001862a697</td>
      <td>New York</td>
      <td>2019-11-14 20:03:27.042 UTC</td>
      <td>40</td>
      <td>True</td>
      <td>900.0</td>
      <td>1320.0</td>
      <td>3483.0</td>
      <td>1</td>
      <td>android</td>
      <td>281.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-6ad45028-c7f2-4aa7-a6e4-31bfb5cad012')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-6ad45028-c7f2-4aa7-a6e4-31bfb5cad012 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-6ad45028-c7f2-4aa7-a6e4-31bfb5cad012');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-00fbbcf6-16d8-42b8-88cd-8bb9f13fcf57">
  <button class="colab-df-quickchart" onclick="quickchart('df-00fbbcf6-16d8-42b8-88cd-8bb9f13fcf57')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-00fbbcf6-16d8-42b8-88cd-8bb9f13fcf57 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




##**Exploratory Data Analysis(EDA)**


```python
df.columns
```




    Index(['session_id', 'search_id', 'user_id', 'search_city', 'search_time',
           'num_of_results', 'is_result', 'median_pickup_walk_time',
           'median_dropoff_walk_time', 'median_bus_travel_time', 'high_demand_val',
           'user_device_os', 'user_device_app_version'],
          dtype='object')




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 569933 entries, 0 to 569932
    Data columns (total 13 columns):
     #   Column                    Non-Null Count   Dtype  
    ---  ------                    --------------   -----  
     0   session_id                569933 non-null  object 
     1   search_id                 569933 non-null  object 
     2   user_id                   569933 non-null  object 
     3   search_city               569933 non-null  object 
     4   search_time               569933 non-null  object 
     5   num_of_results            569933 non-null  int64  
     6   is_result                 569933 non-null  bool   
     7   median_pickup_walk_time   437808 non-null  float64
     8   median_dropoff_walk_time  437808 non-null  float64
     9   median_bus_travel_time    447116 non-null  float64
     10  high_demand_val           569933 non-null  int64  
     11  user_device_os            569642 non-null  object 
     12  user_device_app_version   569642 non-null  float64
    dtypes: bool(1), float64(4), int64(2), object(6)
    memory usage: 52.7+ MB



```python
df.describe()
```





  <div id="df-3f3db83e-fa3a-4d31-9e78-7f9790067f1f" class="colab-df-container">
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
      <th>num_of_results</th>
      <th>median_pickup_walk_time</th>
      <th>median_dropoff_walk_time</th>
      <th>median_bus_travel_time</th>
      <th>high_demand_val</th>
      <th>user_device_app_version</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>569933.000000</td>
      <td>437808.000000</td>
      <td>437808.000000</td>
      <td>447116.000000</td>
      <td>569933.000000</td>
      <td>569642.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>14.916592</td>
      <td>1450.340218</td>
      <td>1071.285838</td>
      <td>3206.170962</td>
      <td>0.671347</td>
      <td>848.746758</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14.759258</td>
      <td>2522.589509</td>
      <td>2224.896520</td>
      <td>1855.138579</td>
      <td>1.658827</td>
      <td>1184.477235</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>57.500000</td>
      <td>0.000000</td>
      <td>44.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>7.000000</td>
      <td>300.000000</td>
      <td>300.000000</td>
      <td>2046.000000</td>
      <td>0.000000</td>
      <td>279.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>10.000000</td>
      <td>600.000000</td>
      <td>570.000000</td>
      <td>3025.500000</td>
      <td>0.000000</td>
      <td>286.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>25.000000</td>
      <td>1260.000000</td>
      <td>1020.000000</td>
      <td>3932.500000</td>
      <td>0.000000</td>
      <td>291.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>100.000000</td>
      <td>65760.000000</td>
      <td>76080.000000</td>
      <td>27923.000000</td>
      <td>10.000000</td>
      <td>3390.000000</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-3f3db83e-fa3a-4d31-9e78-7f9790067f1f')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-3f3db83e-fa3a-4d31-9e78-7f9790067f1f button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-3f3db83e-fa3a-4d31-9e78-7f9790067f1f');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-64441eae-e8f8-49c5-8e4e-3b8fa615aae4">
  <button class="colab-df-quickchart" onclick="quickchart('df-64441eae-e8f8-49c5-8e4e-3b8fa615aae4')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-64441eae-e8f8-49c5-8e4e-3b8fa615aae4 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




###**Check for missing values**


```python
df.shape
```




    (569933, 13)




```python
df.isnull().sum()
```




    session_id                       0
    search_id                        0
    user_id                          0
    search_city                      0
    search_time                      0
    num_of_results                   0
    is_result                        0
    median_pickup_walk_time     132125
    median_dropoff_walk_time    132125
    median_bus_travel_time      122817
    high_demand_val                  0
    user_device_os                 291
    user_device_app_version        291
    dtype: int64




```python
sns.heatmap(df.isnull(),yticklabels=False, cbar=False, cmap='viridis')
```




    <Axes: >




    
![png](feature_eng_files/feature_eng_15_1.png)
    


To handle the missing values, we can delete rows with the missing values.


```python
df.dropna(inplace=True)
```


```python
df.isnull().sum()
```




    session_id                  0
    search_id                   0
    user_id                     0
    search_city                 0
    search_time                 0
    num_of_results              0
    is_result                   0
    median_pickup_walk_time     0
    median_dropoff_walk_time    0
    median_bus_travel_time      0
    high_demand_val             0
    user_device_os              0
    user_device_app_version     0
    dtype: int64




```python
df.shape
```




    (437558, 13)



What is the user device OS?


```python
df.user_device_os.value_counts()
```




    android    350342
    ios         86954
    iOS           262
    Name: user_device_os, dtype: int64



There is ios and iOS which should be the same thing but it comes out with different category, we can replace the iOS to become ios.


```python
df['user_device_os'].replace('iOS', 'ios', inplace=True)
```


```python
df.user_device_os.value_counts()
```




    android    350342
    ios         87216
    Name: user_device_os, dtype: int64




```python
os = df.user_device_os.value_counts().index
```


```python
os_value = df.user_device_os.value_counts().values
```


```python
##Pie Chart
fig_dims = (10, 6)
plt.pie(os_value, labels=os, autopct="%1.2f%%")
```




    ([<matplotlib.patches.Wedge at 0x7e1d35233be0>,
      <matplotlib.patches.Wedge at 0x7e1d35233ac0>],
     [Text(-0.8912889352619149, 0.6446735870808438, 'android'),
      Text(0.8912889352619148, -0.6446735870808439, 'ios')],
     [Text(-0.4861576010519535, 0.3516401384077329, '80.07%'),
      Text(0.48615760105195344, -0.35164013840773295, '19.93%')])




    
![png](feature_eng_files/feature_eng_27_1.png)
    


**The pie chart show that 80.06% of user use android devices, and 19.94% of user use ios devices**

###**Explore Numerical Variables**


```python
df.columns
```




    Index(['session_id', 'search_id', 'user_id', 'search_city', 'search_time',
           'num_of_results', 'is_result', 'median_pickup_walk_time',
           'median_dropoff_walk_time', 'median_bus_travel_time', 'high_demand_val',
           'user_device_os', 'user_device_app_version'],
          dtype='object')




```python
version_category = df.groupby(['user_device_app_version', 'user_device_os']).size().reset_index().rename(columns={0:'user count'})
```


```python
pd.set_option('display.max_rows', None)
version_category
```





  <div id="df-d8639be6-a177-4ee1-9283-137970335b1b" class="colab-df-container">
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
      <th>user_device_app_version</th>
      <th>user_device_os</th>
      <th>user count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>44.0</td>
      <td>android</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>46.0</td>
      <td>android</td>
      <td>39</td>
    </tr>
    <tr>
      <th>2</th>
      <td>49.0</td>
      <td>android</td>
      <td>61</td>
    </tr>
    <tr>
      <th>3</th>
      <td>50.0</td>
      <td>android</td>
      <td>75</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51.0</td>
      <td>android</td>
      <td>67</td>
    </tr>
    <tr>
      <th>5</th>
      <td>54.0</td>
      <td>android</td>
      <td>10</td>
    </tr>
    <tr>
      <th>6</th>
      <td>55.0</td>
      <td>android</td>
      <td>63</td>
    </tr>
    <tr>
      <th>7</th>
      <td>56.0</td>
      <td>android</td>
      <td>40</td>
    </tr>
    <tr>
      <th>8</th>
      <td>57.0</td>
      <td>android</td>
      <td>90</td>
    </tr>
    <tr>
      <th>9</th>
      <td>58.0</td>
      <td>android</td>
      <td>455</td>
    </tr>
    <tr>
      <th>10</th>
      <td>59.0</td>
      <td>android</td>
      <td>4</td>
    </tr>
    <tr>
      <th>11</th>
      <td>61.0</td>
      <td>android</td>
      <td>17</td>
    </tr>
    <tr>
      <th>12</th>
      <td>62.0</td>
      <td>android</td>
      <td>247</td>
    </tr>
    <tr>
      <th>13</th>
      <td>64.0</td>
      <td>android</td>
      <td>78</td>
    </tr>
    <tr>
      <th>14</th>
      <td>65.0</td>
      <td>android</td>
      <td>570</td>
    </tr>
    <tr>
      <th>15</th>
      <td>66.0</td>
      <td>android</td>
      <td>6</td>
    </tr>
    <tr>
      <th>16</th>
      <td>67.0</td>
      <td>android</td>
      <td>9</td>
    </tr>
    <tr>
      <th>17</th>
      <td>68.0</td>
      <td>android</td>
      <td>45</td>
    </tr>
    <tr>
      <th>18</th>
      <td>69.0</td>
      <td>android</td>
      <td>109</td>
    </tr>
    <tr>
      <th>19</th>
      <td>70.0</td>
      <td>android</td>
      <td>39</td>
    </tr>
    <tr>
      <th>20</th>
      <td>71.0</td>
      <td>android</td>
      <td>137</td>
    </tr>
    <tr>
      <th>21</th>
      <td>72.0</td>
      <td>android</td>
      <td>9</td>
    </tr>
    <tr>
      <th>22</th>
      <td>73.0</td>
      <td>android</td>
      <td>14</td>
    </tr>
    <tr>
      <th>23</th>
      <td>74.0</td>
      <td>android</td>
      <td>252</td>
    </tr>
    <tr>
      <th>24</th>
      <td>76.0</td>
      <td>android</td>
      <td>621</td>
    </tr>
    <tr>
      <th>25</th>
      <td>77.0</td>
      <td>android</td>
      <td>95</td>
    </tr>
    <tr>
      <th>26</th>
      <td>78.0</td>
      <td>android</td>
      <td>62</td>
    </tr>
    <tr>
      <th>27</th>
      <td>79.0</td>
      <td>android</td>
      <td>490</td>
    </tr>
    <tr>
      <th>28</th>
      <td>80.0</td>
      <td>android</td>
      <td>1</td>
    </tr>
    <tr>
      <th>29</th>
      <td>81.0</td>
      <td>android</td>
      <td>12</td>
    </tr>
    <tr>
      <th>30</th>
      <td>82.0</td>
      <td>android</td>
      <td>94</td>
    </tr>
    <tr>
      <th>31</th>
      <td>83.0</td>
      <td>android</td>
      <td>110</td>
    </tr>
    <tr>
      <th>32</th>
      <td>84.0</td>
      <td>android</td>
      <td>178</td>
    </tr>
    <tr>
      <th>33</th>
      <td>87.0</td>
      <td>android</td>
      <td>1</td>
    </tr>
    <tr>
      <th>34</th>
      <td>88.0</td>
      <td>android</td>
      <td>5</td>
    </tr>
    <tr>
      <th>35</th>
      <td>89.0</td>
      <td>android</td>
      <td>112</td>
    </tr>
    <tr>
      <th>36</th>
      <td>91.0</td>
      <td>android</td>
      <td>2</td>
    </tr>
    <tr>
      <th>37</th>
      <td>92.0</td>
      <td>android</td>
      <td>58</td>
    </tr>
    <tr>
      <th>38</th>
      <td>93.0</td>
      <td>android</td>
      <td>481</td>
    </tr>
    <tr>
      <th>39</th>
      <td>96.0</td>
      <td>android</td>
      <td>990</td>
    </tr>
    <tr>
      <th>40</th>
      <td>97.0</td>
      <td>android</td>
      <td>273</td>
    </tr>
    <tr>
      <th>41</th>
      <td>254.0</td>
      <td>android</td>
      <td>301</td>
    </tr>
    <tr>
      <th>42</th>
      <td>257.0</td>
      <td>android</td>
      <td>1768</td>
    </tr>
    <tr>
      <th>43</th>
      <td>259.0</td>
      <td>android</td>
      <td>1684</td>
    </tr>
    <tr>
      <th>44</th>
      <td>260.0</td>
      <td>android</td>
      <td>2</td>
    </tr>
    <tr>
      <th>45</th>
      <td>261.0</td>
      <td>android</td>
      <td>4095</td>
    </tr>
    <tr>
      <th>46</th>
      <td>262.0</td>
      <td>android</td>
      <td>1058</td>
    </tr>
    <tr>
      <th>47</th>
      <td>264.0</td>
      <td>android</td>
      <td>10</td>
    </tr>
    <tr>
      <th>48</th>
      <td>265.0</td>
      <td>android</td>
      <td>378</td>
    </tr>
    <tr>
      <th>49</th>
      <td>266.0</td>
      <td>android</td>
      <td>18</td>
    </tr>
    <tr>
      <th>50</th>
      <td>267.0</td>
      <td>android</td>
      <td>4</td>
    </tr>
    <tr>
      <th>51</th>
      <td>269.0</td>
      <td>android</td>
      <td>15</td>
    </tr>
    <tr>
      <th>52</th>
      <td>270.0</td>
      <td>android</td>
      <td>241</td>
    </tr>
    <tr>
      <th>53</th>
      <td>271.0</td>
      <td>android</td>
      <td>32</td>
    </tr>
    <tr>
      <th>54</th>
      <td>272.0</td>
      <td>android</td>
      <td>1920</td>
    </tr>
    <tr>
      <th>55</th>
      <td>273.0</td>
      <td>android</td>
      <td>13</td>
    </tr>
    <tr>
      <th>56</th>
      <td>274.0</td>
      <td>android</td>
      <td>157</td>
    </tr>
    <tr>
      <th>57</th>
      <td>275.0</td>
      <td>android</td>
      <td>3245</td>
    </tr>
    <tr>
      <th>58</th>
      <td>276.0</td>
      <td>android</td>
      <td>25581</td>
    </tr>
    <tr>
      <th>59</th>
      <td>277.0</td>
      <td>android</td>
      <td>34701</td>
    </tr>
    <tr>
      <th>60</th>
      <td>278.0</td>
      <td>android</td>
      <td>10192</td>
    </tr>
    <tr>
      <th>61</th>
      <td>279.0</td>
      <td>android</td>
      <td>22464</td>
    </tr>
    <tr>
      <th>62</th>
      <td>280.0</td>
      <td>android</td>
      <td>15996</td>
    </tr>
    <tr>
      <th>63</th>
      <td>281.0</td>
      <td>android</td>
      <td>6372</td>
    </tr>
    <tr>
      <th>64</th>
      <td>282.0</td>
      <td>android</td>
      <td>544</td>
    </tr>
    <tr>
      <th>65</th>
      <td>283.0</td>
      <td>android</td>
      <td>6801</td>
    </tr>
    <tr>
      <th>66</th>
      <td>284.0</td>
      <td>android</td>
      <td>35704</td>
    </tr>
    <tr>
      <th>67</th>
      <td>285.0</td>
      <td>android</td>
      <td>2189</td>
    </tr>
    <tr>
      <th>68</th>
      <td>286.0</td>
      <td>android</td>
      <td>78513</td>
    </tr>
    <tr>
      <th>69</th>
      <td>287.0</td>
      <td>android</td>
      <td>46</td>
    </tr>
    <tr>
      <th>70</th>
      <td>288.0</td>
      <td>android</td>
      <td>16112</td>
    </tr>
    <tr>
      <th>71</th>
      <td>289.0</td>
      <td>android</td>
      <td>1048</td>
    </tr>
    <tr>
      <th>72</th>
      <td>291.0</td>
      <td>android</td>
      <td>63631</td>
    </tr>
    <tr>
      <th>73</th>
      <td>292.0</td>
      <td>android</td>
      <td>9485</td>
    </tr>
    <tr>
      <th>74</th>
      <td>340.0</td>
      <td>ios</td>
      <td>67</td>
    </tr>
    <tr>
      <th>75</th>
      <td>350.0</td>
      <td>ios</td>
      <td>195</td>
    </tr>
    <tr>
      <th>76</th>
      <td>360.0</td>
      <td>ios</td>
      <td>60</td>
    </tr>
    <tr>
      <th>77</th>
      <td>380.0</td>
      <td>ios</td>
      <td>142</td>
    </tr>
    <tr>
      <th>78</th>
      <td>390.0</td>
      <td>ios</td>
      <td>44</td>
    </tr>
    <tr>
      <th>79</th>
      <td>393.0</td>
      <td>ios</td>
      <td>23</td>
    </tr>
    <tr>
      <th>80</th>
      <td>3100.0</td>
      <td>ios</td>
      <td>86</td>
    </tr>
    <tr>
      <th>81</th>
      <td>3140.0</td>
      <td>ios</td>
      <td>22</td>
    </tr>
    <tr>
      <th>82</th>
      <td>3141.0</td>
      <td>ios</td>
      <td>57</td>
    </tr>
    <tr>
      <th>83</th>
      <td>3143.0</td>
      <td>ios</td>
      <td>19</td>
    </tr>
    <tr>
      <th>84</th>
      <td>3152.0</td>
      <td>ios</td>
      <td>61</td>
    </tr>
    <tr>
      <th>85</th>
      <td>3161.0</td>
      <td>ios</td>
      <td>36</td>
    </tr>
    <tr>
      <th>86</th>
      <td>3170.0</td>
      <td>ios</td>
      <td>108</td>
    </tr>
    <tr>
      <th>87</th>
      <td>3171.0</td>
      <td>ios</td>
      <td>140</td>
    </tr>
    <tr>
      <th>88</th>
      <td>3181.0</td>
      <td>ios</td>
      <td>1</td>
    </tr>
    <tr>
      <th>89</th>
      <td>3184.0</td>
      <td>ios</td>
      <td>207</td>
    </tr>
    <tr>
      <th>90</th>
      <td>3190.0</td>
      <td>ios</td>
      <td>70</td>
    </tr>
    <tr>
      <th>91</th>
      <td>3203.0</td>
      <td>ios</td>
      <td>432</td>
    </tr>
    <tr>
      <th>92</th>
      <td>3210.0</td>
      <td>ios</td>
      <td>472</td>
    </tr>
    <tr>
      <th>93</th>
      <td>3220.0</td>
      <td>ios</td>
      <td>3141</td>
    </tr>
    <tr>
      <th>94</th>
      <td>3240.0</td>
      <td>ios</td>
      <td>347</td>
    </tr>
    <tr>
      <th>95</th>
      <td>3241.0</td>
      <td>ios</td>
      <td>7341</td>
    </tr>
    <tr>
      <th>96</th>
      <td>3261.0</td>
      <td>ios</td>
      <td>11375</td>
    </tr>
    <tr>
      <th>97</th>
      <td>3290.0</td>
      <td>ios</td>
      <td>41</td>
    </tr>
    <tr>
      <th>98</th>
      <td>3291.0</td>
      <td>ios</td>
      <td>5420</td>
    </tr>
    <tr>
      <th>99</th>
      <td>3301.0</td>
      <td>ios</td>
      <td>20554</td>
    </tr>
    <tr>
      <th>100</th>
      <td>3340.0</td>
      <td>ios</td>
      <td>11630</td>
    </tr>
    <tr>
      <th>101</th>
      <td>3390.0</td>
      <td>ios</td>
      <td>25125</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-d8639be6-a177-4ee1-9283-137970335b1b')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-d8639be6-a177-4ee1-9283-137970335b1b button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-d8639be6-a177-4ee1-9283-137970335b1b');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-723f9e2c-e23a-44e6-9643-4290a08edacb">
  <button class="colab-df-quickchart" onclick="quickchart('df-723f9e2c-e23a-44e6-9643-4290a08edacb')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-723f9e2c-e23a-44e6-9643-4290a08edacb button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




**There are 78505 users use the android version of 286.0**

**There are 24944 users use the ios version of 3390.0**


```python
import matplotlib
matplotlib.rcParams['figure.figsize'] = (50, 20)
sns.barplot(x="user_device_app_version", y="user count", hue='user_device_os', data = version_category, palette=['red', 'green'])
```




    <Axes: xlabel='user_device_app_version', ylabel='user count'>




    
![png](feature_eng_files/feature_eng_34_1.png)
    


##**Feature Selection**

**Filter features by Correlation**

Since the column "is_result" is boolean data type, and the default value of heatmap is numeric_only, we can drop the feature and save it in a new dataframe containing only the numeric value.


```python
df_copy = df.copy()
bool_col = df_copy.select_dtypes(include=bool).columns
df_no_bool = df_copy.drop(columns = bool_col)

fig_dims = (12, 8)
fig, ax = plt.subplots(figsize=fig_dims)
sns.heatmap(df_no_bool.corr(), ax=ax)
plt.show()
```

    <ipython-input-23-3c9bddae7265>:7: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
      sns.heatmap(df_no_bool.corr(), ax=ax)



    
![png](feature_eng_files/feature_eng_38_1.png)
    



```python
abs(df_no_bool.corr()["high_demand_val"])
```

    <ipython-input-24-e1926fc73067>:1: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
      abs(df_no_bool.corr()["high_demand_val"])





    num_of_results              0.157267
    median_pickup_walk_time     0.013909
    median_dropoff_walk_time    0.048582
    median_bus_travel_time      0.026032
    high_demand_val             1.000000
    user_device_app_version     0.012354
    Name: high_demand_val, dtype: float64



The correlation analysis reveals the relationship between the 'high_demand_val' column, indicating limited bus availability, and other features. Notably, 'num_of_results' shows a positive correlation (0.155831), suggesting a modest association with the number of available bus results. Additionally, 'median_pickup_walk_time' (0.013749), 'median_dropoff_walk_time' (0.047770), 'median_bus_travel_time' (0.028420), and 'user_device_app_version' (0.011027) exhibit relatively weak correlations with 'high_demand_val'. The strongest correlation is observed with 'num_of_results', implying a potential connection between bus availability and the quantity of search results.

##**Feature Preprocessing**

Handling outliers using the winsorization technique and normalizing the numeric features using StandardScaler.


```python
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from scipy.stats.mstats import winsorize

# Deal with outliers (using a simple example, you might need more sophisticated methods)
# For demonstration purposes, we'll winsorize the numeric features
numeric_features = df_no_bool.select_dtypes(include=[np.number]).columns
df_no_bool[numeric_features] = df_no_bool[numeric_features].apply(lambda x: winsorize(x, limits=[0.05, 0.05]))

# Normalize data using StandardScaler
scaler = StandardScaler()
df_no_bool[numeric_features] = scaler.fit_transform(df_no_bool[numeric_features])

# Check the correlation again after handling outliers and normalization
fig_dims = (12, 8)
fig, ax = plt.subplots(figsize=fig_dims)
sns.heatmap(df_no_bool.corr(), ax=ax)
plt.show()

# Check correlation with the target variable again
correlation_with_target_after_preprocessing = abs(df_no_bool.corr()["high_demand_val"])
print(correlation_with_target_after_preprocessing)
```

    <ipython-input-25-268365a9a57c>:16: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
      sns.heatmap(df_no_bool.corr(), ax=ax)



    
![png](feature_eng_files/feature_eng_43_1.png)
    


    num_of_results              0.161151
    median_pickup_walk_time     0.017008
    median_dropoff_walk_time    0.074036
    median_bus_travel_time      0.003224
    high_demand_val             1.000000
    user_device_app_version     0.007087
    Name: high_demand_val, dtype: float64


    <ipython-input-25-268365a9a57c>:20: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
      correlation_with_target_after_preprocessing = abs(df_no_bool.corr()["high_demand_val"])


The resulting correlation analysis reveals the correlation coefficients between 'high_demand_val' and other features after these preprocessing steps. Notably, the features 'num_of_results,' 'median_pickup_walk_time,' 'median_dropoff_walk_time,' and 'user_device_app_version' exhibit positive correlations, suggesting potential associations with the likelihood of high demand for bus seats.

##**Feature Transformation**

**Log Transformation**


```python
from scipy.stats import skew
unwanted_columns = ['session_id', 'search_id', 'user_id', 'search_city', 'search_time', 'user_device_os']  # Replace with the actual column names you want to drop

# Drop unwanted columns
df_sample = df_no_bool.drop(columns=unwanted_columns)

# Select numeric features
num_features = df_sample.select_dtypes(include=[np.number]).columns

# Logarithmic transformation for skewed numeric features
skewed_features = df_sample[num_features].apply(lambda x: np.abs(skew(x)))  # Use absolute skewness
skewed_features = skewed_features[skewed_features > 0.5]  # Threshold for skewness

# Apply log transformation to skewed numeric features
df_sample[skewed_features.index] = np.log1p(df_sample[skewed_features.index])

# Check the transformed DataFrame
print(df_sample.head())

# Visualize the correlation after transformation
fig_dims = (12, 8)
fig, ax = plt.subplots(figsize=fig_dims)
sns.heatmap(df_sample.corr(), ax=ax)
plt.show()

```

    /usr/local/lib/python3.10/dist-packages/pandas/core/internals/blocks.py:351: RuntimeWarning: invalid value encountered in log1p
      result = func(self.values, **kwargs)


       num_of_results  median_pickup_walk_time  median_dropoff_walk_time  \
    0             NaN                -0.187859                  0.557156   
    1        0.663949                -1.297382                  0.614547   
    2             NaN                -0.146607                  0.435662   
    3             NaN                -0.812884                 -0.781274   
    4        0.663949                -0.280974                  0.405977   
    
       median_bus_travel_time  high_demand_val  user_device_app_version  
    0                0.441813        -1.385421                 0.752659  
    1               -1.215738        -1.385421                -1.149900  
    2                0.958925        -1.385421                 0.752659  
    3                0.637705        -1.385421                -1.160319  
    4                0.302152         0.152040                -1.176220  



    
![png](feature_eng_files/feature_eng_47_2.png)
    


The transformation is applied to the columns 'num_of_results,' 'median_pickup_walk_time,' 'median_dropoff_walk_time,' 'median_bus_travel_time,' 'high_demand_val,' and 'user_device_app_version.'

**Positive values:** For values greater than 0, the logarithmic transformation compresses higher values more than lower values. This can help to make the distribution more symmetric and conform to assumptions of normality.

**Negative values or zero:** Logarithmic transformation is not defined for non-positive values. This is why NaN values might appear in the output for columns like 'num_of_results.'

##**Feature Creation**


```python
# Convert the search_time column to a pandas datetime object
df['timestamp'] = pd.to_datetime(df['search_time'])
```


```python
# Extract day of the week, month, and year features
df['day_of_week'] = df['timestamp'].dt.dayofweek  # Monday is 0 and Sunday is 6
df['month'] = df['timestamp'].dt.month
df['year'] = df['timestamp'].dt.year

df.head()
```





  <div id="df-b1328e03-65aa-441d-a308-d4fc5dde5341" class="colab-df-container">
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
      <th>session_id</th>
      <th>search_id</th>
      <th>user_id</th>
      <th>search_city</th>
      <th>search_time</th>
      <th>num_of_results</th>
      <th>is_result</th>
      <th>median_pickup_walk_time</th>
      <th>median_dropoff_walk_time</th>
      <th>median_bus_travel_time</th>
      <th>high_demand_val</th>
      <th>user_device_os</th>
      <th>user_device_app_version</th>
      <th>timestamp</th>
      <th>day_of_week</th>
      <th>month</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>911ab421-5800-401f-8045-4427c51cc351</td>
      <td>375890ed-3e8b-400f-b40b-bab770022e5b</td>
      <td>5d6d32ebf321e600193e3d39</td>
      <td>New York</td>
      <td>2020-02-16 13:47:25.811 UTC</td>
      <td>10</td>
      <td>True</td>
      <td>1020.0</td>
      <td>1680.0</td>
      <td>3673.0</td>
      <td>0</td>
      <td>ios</td>
      <td>3390.0</td>
      <td>2020-02-16 13:47:25.811000+00:00</td>
      <td>6</td>
      <td>2</td>
      <td>2020</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ce7a234f-ddeb-4de0-844f-bcfd194ca1f5</td>
      <td>aa82ffda-c53e-4e48-a39f-87c4df5d102c</td>
      <td>5d8073b18743200019da237c</td>
      <td>New York</td>
      <td>2019-12-10 19:49:25.792 UTC</td>
      <td>40</td>
      <td>True</td>
      <td>300.0</td>
      <td>1860.0</td>
      <td>1418.0</td>
      <td>0</td>
      <td>android</td>
      <td>286.0</td>
      <td>2019-12-10 19:49:25.792000+00:00</td>
      <td>1</td>
      <td>12</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8bd1472e-404a-489f-a8aa-c4633d51929a</td>
      <td>6ee93693-ff10-49d0-8f38-cc89ac6f0b18</td>
      <td>59ddadd78f279c000f6e15b0</td>
      <td>New York</td>
      <td>2020-02-23 16:26:56.543 UTC</td>
      <td>10</td>
      <td>True</td>
      <td>1080.0</td>
      <td>1380.0</td>
      <td>4376.5</td>
      <td>0</td>
      <td>ios</td>
      <td>3390.0</td>
      <td>2020-02-23 16:26:56.543000+00:00</td>
      <td>6</td>
      <td>2</td>
      <td>2020</td>
    </tr>
    <tr>
      <th>3</th>
      <td>711c199e-23e7-450a-8482-ee36b78bf291</td>
      <td>6ea972a3-28d9-4bb6-9100-4acfba900af5</td>
      <td>5ce898dfbcc3ed001a3de358</td>
      <td>New York</td>
      <td>2019-12-05 07:55:20.539 UTC</td>
      <td>10</td>
      <td>True</td>
      <td>480.0</td>
      <td>480.0</td>
      <td>3939.5</td>
      <td>0</td>
      <td>android</td>
      <td>284.0</td>
      <td>2019-12-05 07:55:20.539000+00:00</td>
      <td>3</td>
      <td>12</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3f2ea46a-a082-4eeb-9722-003e1461a10c</td>
      <td>2ee71414-2596-43f8-b67d-0d2846d953bb</td>
      <td>5ca5e5a87c646d001862a697</td>
      <td>New York</td>
      <td>2019-11-14 20:03:27.042 UTC</td>
      <td>40</td>
      <td>True</td>
      <td>900.0</td>
      <td>1320.0</td>
      <td>3483.0</td>
      <td>1</td>
      <td>android</td>
      <td>281.0</td>
      <td>2019-11-14 20:03:27.042000+00:00</td>
      <td>3</td>
      <td>11</td>
      <td>2019</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-b1328e03-65aa-441d-a308-d4fc5dde5341')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-b1328e03-65aa-441d-a308-d4fc5dde5341 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-b1328e03-65aa-441d-a308-d4fc5dde5341');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-1d6f6298-bbb1-4363-a804-f5b385765b96">
  <button class="colab-df-quickchart" onclick="quickchart('df-1d6f6298-bbb1-4363-a804-f5b385765b96')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-1d6f6298-bbb1-4363-a804-f5b385765b96 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




These time-based features can be particularly useful for understanding how patterns vary over different days, months, or years in your time series data.

##**Visualization**


```python
# Pairplot to visualize relationships between numeric features
sns.pairplot(df_sample)
plt.show()

# Boxplot to visualize the distribution of a specific feature
sns.boxplot(x='high_demand_val', data=df_sample)
plt.show()

# Heatmap to visualize the correlation between features
fig_dims = (12, 8)
fig, ax = plt.subplots(figsize=fig_dims)
sns.heatmap(df_sample.corr(), ax=ax, annot=True)
plt.show()

# Histogram to visualize the distribution of a specific feature
sns.histplot(df_sample['median_pickup_walk_time'], kde=True)
plt.show()
```


    
![png](feature_eng_files/feature_eng_54_0.png)
    



    
![png](feature_eng_files/feature_eng_54_1.png)
    



    
![png](feature_eng_files/feature_eng_54_2.png)
    



    
![png](feature_eng_files/feature_eng_54_3.png)
    


##**Conclusion**

In conclusion, the feature engineering process involved several key steps aimed at enhancing the dataset for improved model performance and interpretability.

1. Handling Missing Values:

Addressed missing values in the dataset, using appropriate techniques such as imputation or removal, depending on the nature of the missing data. This ensures a more complete and reliable dataset.

2. Dealing with Outliers:

Utilized winsorization to handle outliers in numeric features. Winsorization involves limiting extreme values to be within a specified range, reducing the impact of outliers on model performance.

3. Normalization of Numeric Features:

Applied normalization using StandardScaler to ensure that numeric features are on a similar scale. This step is essential for models that are sensitive to the scale of input features, promoting better convergence and performance.

4. Logarithmic Transformation for Skewed Numeric Features:

Addressed skewness in numeric features through logarithmic transformations. Skewed data can negatively impact the performance of certain models, and the logarithmic transformation helps in achieving a more symmetric distribution.

5. Feature Creation:

Created new features to capture additional information and patterns in the data. Techniques such as interaction terms, polynomial features, binning, and aggregation were applied based on the nature of the data and the problem domain.

Time-Based Features:

Extracted time-based features, including day of the week, month, and year, from timestamp data. This is particularly relevant when dealing with time series data, allowing models to capture temporal patterns.

6. Visualization:

Employed various visualization techniques to gain insights into the distribution of features and relationships between them. Visualizations such as pairplots, boxplots, heatmaps, and histograms were used to explore patterns and guide further analysis.

The decisions made in these feature engineering steps were driven by a combination of domain knowledge, statistical considerations, and the specific requirements of the machine learning task at hand. Each step aimed to address challenges in the data, improve the quality of features, and prepare the dataset for effective model training and evaluation. The iterative nature of feature engineering involves continuous refinement based on insights gained from the data exploration process.
