
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise 4: EDA - Descriptive Statistics

The steps to calculate summary statistics for numerical columns using pandas methods like `describe()`, `mean()`, `median()`, and `std()`. We will also create frequency tables for categorical columns.

### Step 1: Calculate Summary Statistics for Numerical Columns

1. **Load the Titanic Dataset:**
   - Ensure the dataset is loaded into a pandas DataFrame.
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Use the describe() Method:**
   - The `describe()` method provides a summary of statistics for numerical columns.
   ```python
   df.describe()
   ```

3. **Calculate Mean, Median, and Standard Deviation:**
   - Use the `mean()`, `median()`, and `std()` methods to calculate these statistics for numerical columns.
   ```python
   mean_values = df.mean()
   median_values = df.median()
   std_values = df.std()
   ```

### Step 2: Create Frequency Tables for Categorical Columns

1. **Identify Categorical Columns:**
   - Use the `select_dtypes()` method to select columns with object data type (typically used for categorical data).
   ```python
   categorical_columns = df.select_dtypes(include=['object']).columns
   ```

2. **Create Frequency Tables:**
   - Use the `value_counts()` method to create frequency tables for each categorical column.
   ```python
   frequency_tables = {col: df[col].value_counts() for col in categorical_columns}
   ```

### Step-by-Step Execution

1. **Load the Titanic Dataset:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Use the describe() Method:**
   ```python
   summary_statistics = df.describe()
   print(summary_statistics)
   ```

3. **Calculate Mean, Median, and Standard Deviation:**
   ```python
   mean_values = df.mean()
   median_values = df.median()
   std_values = df.std()

   print("Mean Values:\n", mean_values)
   print("Median Values:\n", median_values)
   print("Standard Deviation Values:\n", std_values)
   ```

4. **Identify Categorical Columns:**
   ```python
   categorical_columns = df.select_dtypes(include=['object']).columns
   print("Categorical Columns:\n", categorical_columns)
   ```

5. **Create Frequency Tables:**
   ```python
   frequency_tables = {col: df[col].value_counts() for col in categorical_columns}
   for col, freq_table in frequency_tables.items():
       print(f"Frequency Table for {col}:\n{freq_table}\n")
   ```

### Full Code
Here's the complete code in a single notebook:

1. **Code Cell 1: Load the Titanic Dataset**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Code Cell 2: Use the describe() Method**
   ```python
   summary_statistics = df.describe()
   print(summary_statistics)
   ```

3. **Code Cell 3: Calculate Mean, Median, and Standard Deviation**
   ```python
   mean_values = df.mean()
   median_values = df.median()
   std_values = df.std()

   print("Mean Values:\n", mean_values)
   print("Median Values:\n", median_values)
   print("Standard Deviation Values:\n", std_values)
   ```

4. **Code Cell 4: Identify Categorical Columns**
   ```python
   categorical_columns = df.select_dtypes(include=['object']).columns
   print("Categorical Columns:\n", categorical_columns)
   ```

5. **Code Cell 5: Create Frequency Tables**
   ```python
   frequency_tables = {col: df[col].value_counts() for col in categorical_columns}
   for col, freq_table in frequency_tables.items():
       print(f"Frequency Table for {col}:\n{freq_table}\n")
   ```

By following these steps, you will have calculated summary statistics for numerical columns and created frequency tables for categorical columns in the Titanic dataset.


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

