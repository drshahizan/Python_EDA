
# Assignment 5: Automated Feature Engineering Tools - TPOT

<div align="center">
  <img src="assignment/ass5/hpdp/ANGKASA/Tool 1 - TPOT/tpot-pipeline-example-768x361.png" alt="tsfresh">
</div>


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
# Drop rows with missing values in either column 'acre_lot' or 'zip_code'
data = data.dropna(subset=['acre_lot', 'zip_code'])
```

```python
# Drop the column 'prev_sold_date' and 'status' as it is irrelevent
data = data.drop('prev_sold_date', axis=1)
data = data.drop('status', axis=1)
```

### 4. Feature Engineering with TPOT:

Install TPOT using the following command:

```python
!pip install tpot
```

Now, use TPOT to automatically optimize the machine learning pipeline:

```python
from tpot import TPOTRegressor
from sklearn.model_selection import train_test_split
from sklearn.impute import SimpleImputer

# Split the Data into Features and Target
X = df.drop('price', axis=1)
y = df['price']

# Train-Test Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Impute null values with mean
imputer = SimpleImputer(strategy='mean')
X_train_numeric = X_train.select_dtypes(include=['number'])
X_train[X_train_numeric.columns] = imputer.fit_transform(X_train_numeric)

# Drop unnecessary non-numeric columns
non_numeric_columns = X_train.select_dtypes(exclude=['number']).columns
X_train = X_train.drop(columns=non_numeric_columns)

# Run TPOT
tpot = TPOTRegressor(verbosity=2, generations=5, population_size=20, random_state=42, n_jobs=-1)
tpot.fit(X_train, y_train)

# Evaluate the model
tpot.fitted_pipeline_.steps[-1][1].feature_importances_

import matplotlib.pyplot as plt

feature_importances = tpot.fitted_pipeline_.steps[-1][1].feature_importances_
features = X_train.columns
plt.bar(features, feature_importances)
plt.xticks(rotation='vertical')
plt.show()

tpot.fitted_pipeline_.graphviz()

```

### 5. Feature Selection with TPOT:

After extracting features, you may want to perform feature selection based on importance or other criteria.

```python
# tpot_fs = TPOTRegressor(verbosity=2, generations=5, population_size=20, random_state=42, n_jobs=-1,
                        config_dict='TPOT sparse', memory='auto', periodic_checkpoint_folder='/content/gdrive/MyDrive/tpot_checkpoint')

tpot_fs.fit(X_train, y_train)

# Get the best pipeline
best_model_fs = tpot_fs.fitted_pipeline_

# Apply feature selection on the dataset
from sklearn.feature_selection import SelectFromModel
feature_selector = SelectFromModel(best_model_fs.steps[-1][1], prefit=True)
X_train_selected = feature_selector.transform(X_train)
X_test_selected = feature_selector.transform(X_test)

# 6. Visualization:

Visualize the distribution of selected features:

```python
# Visualize the distribution of a specific feature
import matplotlib.pyplot as plt

feature_to_visualize = 'price__median'
plt.hist(X_train_selected[feature_to_visualize])
plt.title(f'Distribution of {feature_to_visualize}')
plt.show()
```

### 6. Conclusion:

In conclusion, leveraging TPOT for automated machine learning proved to be a valuable approach in streamlining the feature engineering process. TPOT's genetic programming capabilities allowed for an exhaustive exploration of diverse combinations of preprocessing steps, feature selections, and regression models, ultimately leading to the discovery of an optimized machine learning pipeline.

Throughout the process, TPOT intelligently navigated the feature engineering landscape, adapting its search strategy to the unique characteristics of the dataset. The automation included handling missing values, encoding categorical variables, and selecting relevant features, all vital steps in preparing the data for regression modeling.

The decision to use TPOT for feature engineering was motivated by its ability to:

Automate Model Selection: TPOT's genetic programming systematically explored a variety of regression models, identifying the one that best suited the dataset. This eliminated the need for manual model selection, ensuring a comprehensive search across the model space.

Optimize Hyperparameters: TPOT not only chose the best model but also fine-tuned its hyperparameters. This automated hyperparameter optimization contributed to the overall performance improvement of the selected model.

Handle Complex Pipelines: TPOT's flexibility allowed it to consider complex machine learning pipelines, including diverse preprocessing steps. This adaptability was crucial in addressing the intricacies of the dataset without the need for manual intervention.

Enhance Reproducibility: The use of TPOT with specified random seeds ensured reproducibility, enabling consistent results across different runs and facilitating the tracking of the feature engineering and model selection process.

In summary, the application of TPOT for feature engineering provided a robust, automated solution that not only saved time and effort but also unearthed a high-performing machine learning pipeline. The decisions to automate feature engineering with TPOT were driven by the desire to efficiently explore the feature space, optimize model performance, and maintain a reproducible and adaptable workflow in the regression modeling task.
