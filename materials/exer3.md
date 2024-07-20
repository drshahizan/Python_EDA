
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise 3: Data Cleaning and Preprocessing

Here are the processes for identifying and handling missing values in the Titanic dataset using methods such as `dropna()` and `fillna()`. We will also transform data types as necessary.


### Step 1: Identify Missing Values
1. **Check for Missing Values:**
   - After loading the dataset into a pandas DataFrame, we can use the `isnull()` and `sum()` methods to check for missing values.
   ```python
   df.isnull().sum()
   ```

### Step 2: Handle Missing Values
1. **Decide on a Strategy:**
   - We can either remove rows/columns with missing values using `dropna()` or fill missing values using `fillna()`.

2. **Remove Missing Values:**
   - To remove rows with any missing values, use `dropna()`.
   ```python
   df_dropped = df.dropna()
   ```
   - To remove columns with any missing values, use:
   ```python
   df_dropped_cols = df.dropna(axis=1)
   ```

3. **Fill Missing Values:**
   - To fill missing values, we can use `fillna()`. For example, we can fill missing values in the `Age` column with the mean age:
   ```python
   df['Age'].fillna(df['Age'].mean(), inplace=True)
   ```
   - We can fill missing values in the `Embarked` column with the most frequent value:
   ```python
   df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
   ```

### Step 3: Convert Data Types if Necessary
1. **Check Data Types:**
   - Use `dtypes` to check the data types of each column.
   ```python
   df.dtypes
   ```

2. **Convert Data Types:**
   - If needed, we can convert data types using the `astype()` method. For example, converting the `Survived` column to `bool`:
   ```python
   df['Survived'] = df['Survived'].astype(bool)
   ```

### Step-by-Step Execution

1. **Check for Missing Values:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   missing_values = df.isnull().sum()
   print(missing_values)
   ```

2. **Handle Missing Values:**

   - **Fill Missing Values:**
     ```python
     df['Age'].fillna(df['Age'].mean(), inplace=True)
     df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
     ```

   - **Drop Rows/Columns with Missing Values (if needed):**
     ```python
     df_dropped = df.dropna()  # To drop rows with any missing values
     # df_dropped_cols = df.dropna(axis=1)  # To drop columns with any missing values
     ```

3. **Convert Data Types if Necessary:**
   ```python
   print(df.dtypes)
   df['Survived'] = df['Survived'].astype(bool)
   ```

### Full Code
Here's the complete code in a single notebook:

1. **Code Cell 1:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Code Cell 2:**
   ```python
   missing_values = df.isnull().sum()
   print(missing_values)
   ```

3. **Code Cell 3:**
   ```python
   df['Age'].fillna(df['Age'].mean(), inplace=True)
   df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
   ```

4. **Code Cell 4:**
   ```python
   df_dropped = df.dropna()  # Uncomment if you prefer to drop rows with any missing values
   # df_dropped_cols = df.dropna(axis=1)  # Uncomment if you prefer to drop columns with any missing values
   ```

5. **Code Cell 5:**
   ```python
   print(df.dtypes)
   df['Survived'] = df['Survived'].astype(bool)
   ```

6. **Code Cell 6 (Optional): Display the First Few Rows:**
   ```python
   df.head()
   ```

By following these steps, you will have identified and handled missing values in the Titanic dataset and converted data types if necessary.


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

