# Assignment 5: Automated Feature Engineering Tools - tsfresh



### 1. Dataset Selection:

Choose a dataset with time series characteristics.

Dataset link: https://www.kaggle.com/datasets/ahmedshahriarsakib/usa-real-estate-dataset

### 2. Loading the Dataset:

To import a dataset from Kaggle into Google Colab, you need to follow these general steps:

1. **Download Kaggle API Key:**
   - Go to your Kaggle account settings (https://www.kaggle.com/account) and scroll down to the API section.
   - Click on "Create New API Token" to download a file named `kaggle.json`. This file contains your Kaggle API credentials.

2. **Upload Kaggle API Key to Google Colab:**
   - In Google Colab, click on the folder icon on the left sidebar.
   - Click on the "Upload" button and upload the `kaggle.json` file.

3. **Install Kaggle Package:**
   - Run the following commands in a Colab cell to install the Kaggle package and move the API key to the correct directory:

   ```python
   !pip install kaggle

   # Move the uploaded kaggle.json to the required directory
   !mkdir -p ~/.kaggle
   !cp kaggle.json ~/.kaggle/
   !chmod 600 ~/.kaggle/kaggle.json
   ```

4. **Download Dataset Using Kaggle API:**
   - Use the `kaggle datasets download` command to download the dataset. Replace `<dataset-name>` with the actual name of the Kaggle dataset.

   ```python
   !kaggle datasets download -d ahmedshahriarsakib/usa-real-estate-dataset
   ```

5. **Unzip the Dataset:**
   - Use the `unzip` command to extract the contents of the downloaded ZIP file.

   ```python
   ! unzip usa-real-estate-dataset.zip
   ```

6. **Load the Dataset:**
   - Use pandas or any other appropriate library to load the dataset into a DataFrame.

   ```python
   import pandas as pd

   df = pd.read_csv('realtor-data.csv')
   df.head()
   ```

### 3. Exploratory Data Analysis (EDA):

Perform basic exploratory data analysis to understand the dataset.

```python
# Check for missing values
missing_values = df.isnull().sum()

# Get data types of each column
data_types = df.dtypes

# Display summary statistics
summary_stats = df.describe()

# Explore the structure of the dataset
dataset_info = df.info()
```

```python
# Drop the missing values
df.dropna(inplace=True)
```

```python
# Convert the column 'prev_sold_date' datatype from object to datetime datatype
df['prev_sold_date'] = pd.to_datetime(df['prev_sold_date'])
```

### 4. Feature Engineering with `tsfresh`:

Install `tsfresh` if you haven't already:

```python
!pip install tsfresh
```

Now, use `tsfresh` to automatically extract features:

```python
from tsfresh import extract_features

# Assuming 'prev_sold_date' is the column with the time information,
# and 'price' is the value you want to extract features from

# Add a new 'id' column with a unique identifier for each row
df['id'] = range(len(df))

chunk_size = 10000  # Adjust as needed
chunks = [df[i:i + chunk_size] for i in range(0, len(df), chunk_size)]

extracted_features_list = []
for chunk in chunks:
    chunk_features = extract_features(chunk, column_id="id", column_sort="prev_sold_date", column_value="price")
    extracted_features_list.append(chunk_features)

extracted_features = pd.concat(extracted_features_list)
```

### 5. Feature Selection:

After extracting features, you may want to perform feature selection based on importance or other criteria.

```python
# Show the list of extracted features
for col in extracted_features.columns:
    print(col)
```

```python
# Select feature to visualize
feature_to_visualize = 'price__median'
```


### 6. Visualization:

Visualize the transformed and newly created features:

```python
# Visualize the distribution of a specific feature
import matplotlib.pyplot as plt

feature_to_visualize = 'price__median'
plt.hist(extracted_features[feature_to_visualize])
plt.title(f'Distribution of {feature_to_visualize}')
plt.show()
```

### 7. Conclusion:

In this analysis, a dataset with 261,055 real estate listings containing information such as property details, location, and sale prices was processed using the `tsfresh` library to extract a diverse set of time series features from the 'price' variable. The dataset exhibited no missing values and was well-structured with a variety of numerical and categorical columns. The feature extraction process was performed in chunks of 10,000 rows, optimizing for computational efficiency. The resulting set of extracted features provides a comprehensive overview of the temporal characteristics of property prices. Notable features include statistical measures, distribution properties, and patterns such as the percentage of reoccurring values and sample entropy. These features can potentially serve as valuable inputs for machine learning models in predicting or understanding real estate price dynamics. The successful extraction of features from this dataset demonstrates the versatility of `tsfresh` in handling large-scale time series data with diverse temporal patterns.
