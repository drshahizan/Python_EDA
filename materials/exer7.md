
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise 7: Identifying Outliers

The steps to identify outliers in numerical data using statistical methods and visualizations like box plots. We'll also explore techniques to handle outliers, such as removing them or transforming the data, using the Titanic dataset.

### Step 1: Load the Titanic Dataset
1. **Load the dataset:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

### Step 2: Identify Outliers Using Box Plots
1. **Import Matplotlib and Seaborn:**
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns
   ```

2. **Create box plots for numerical columns:**
   ```python
   numerical_columns = df.select_dtypes(include=['float64', 'int64']).columns

   plt.figure(figsize=(15, 10))
   for i, col in enumerate(numerical_columns, 1):
       plt.subplot(3, 3, i)
       sns.boxplot(y=col, data=df)
       plt.title(f'Box Plot of {col}')
   plt.tight_layout()
   plt.show()
   ```

### Step 3: Identify Outliers Using the IQR Method
1. **Calculate the IQR and identify outliers:**
   ```python
   def find_outliers(df, col):
       Q1 = df[col].quantile(0.25)
       Q3 = df[col].quantile(0.75)
       IQR = Q3 - Q1
       lower_bound = Q1 - 1.5 * IQR
       upper_bound = Q3 + 1.5 * IQR
       outliers = df[(df[col] < lower_bound) | (df[col] > upper_bound)]
       return outliers

   for col in numerical_columns:
       outliers = find_outliers(df, col)
       print(f'Outliers in {col}:')
       print(outliers)
   ```

### Step 4: Handle Outliers
1. **Option 1: Remove Outliers**
   ```python
   def remove_outliers(df, col):
       Q1 = df[col].quantile(0.25)
       Q3 = df[col].quantile(0.75)
       IQR = Q3 - Q1
       lower_bound = Q1 - 1.5 * IQR
       upper_bound = Q3 + 1.5 * IQR
       df = df[(df[col] >= lower_bound) & (df[col] <= upper_bound)]
       return df

   for col in numerical_columns:
       df = remove_outliers(df, col)
   ```

2. **Option 2: Transform Data (e.g., Log Transformation)**
   ```python
   import numpy as np

   df_transformed = df.copy()
   for col in numerical_columns:
       df_transformed[col] = np.log1p(df_transformed[col])

   # Plot transformed data
   plt.figure(figsize=(15, 10))
   for i, col in enumerate(numerical_columns, 1):
       plt.subplot(3, 3, i)
       sns.boxplot(y=col, data=df_transformed)
       plt.title(f'Box Plot of Transformed {col}')
   plt.tight_layout()
   plt.show()
   ```

### Step-by-Step Execution

1. **Load the Titanic Dataset:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Import Matplotlib and Seaborn:**
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns
   ```

3. **Create Box Plots for Numerical Columns:**
   ```python
   numerical_columns = df.select_dtypes(include=['float64', 'int64']).columns

   plt.figure(figsize=(15, 10))
   for i, col in enumerate(numerical_columns, 1):
       plt.subplot(3, 3, i)
       sns.boxplot(y=col, data=df)
       plt.title(f'Box Plot of {col}')
   plt.tight_layout()
   plt.show()
   ```

4. **Identify Outliers Using the IQR Method:**
   ```python
   def find_outliers(df, col):
       Q1 = df[col].quantile(0.25)
       Q3 = df[col].quantile(0.75)
       IQR = Q3 - Q1
       lower_bound = Q1 - 1.5 * IQR
       upper_bound = Q3 + 1.5 * IQR
       outliers = df[(df[col] < lower_bound) | (df[col] > upper_bound)]
       return outliers

   for col in numerical_columns:
       outliers = find_outliers(df, col)
       print(f'Outliers in {col}:')
       print(outliers)
   ```

5. **Handle Outliers - Option 1: Remove Outliers:**
   ```python
   def remove_outliers(df, col):
       Q1 = df[col].quantile(0.25)
       Q3 = df[col].quantile(0.75)
       IQR = Q3 - Q1
       lower_bound = Q1 - 1.5 * IQR
       upper_bound = Q3 + 1.5 * IQR
       df = df[(df[col] >= lower_bound) & (df[col] <= upper_bound)]
       return df

   for col in numerical_columns:
       df = remove_outliers(df, col)
   ```

6. **Handle Outliers - Option 2: Transform Data (e.g., Log Transformation):**
   ```python
   import numpy as np

   df_transformed = df.copy()
   for col in numerical_columns:
       df_transformed[col] = np.log1p(df_transformed[col])

   # Plot transformed data
   plt.figure(figsize=(15, 10))
   for i, col in enumerate(numerical_columns, 1):
       plt.subplot(3, 3, i)
       sns.boxplot(y=col, data=df_transformed)
       plt.title(f'Box Plot of Transformed {col}')
   plt.tight_layout()
   plt.show()
   ```

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

