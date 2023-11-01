
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# Pandas

Pandas is a popular Python library for data manipulation and analysis, and it offers a wide range of functionalities that are particularly useful for conducting Exploratory Data Analysis (EDA). Here are some common pandas syntax and functions suitable for EDA:

1. **Loading Data:**
   - Read data from various file formats (e.g., CSV, Excel, SQL database):

      ```python
      import pandas as pd
      df = pd.read_csv('data.csv')
      ```

2. **Data Summary:**
   - Get basic information about the dataset:

   ```python
   df.info()
   ```

   - Display summary statistics for numerical columns:

   ```python
   df.describe()
   ```

   - View the first few rows of the dataset:

   ```python
   df.head()
   ```

3. **Data Cleaning and Handling:**
   - Handle missing values:

   ```python
   df.isna().sum()  # Check for missing values
   df.dropna()       # Drop rows with missing values
   df.fillna(value)  # Fill missing values with a specified value
   ```

   - Remove duplicates:

   ```python
   df.drop_duplicates()
   ```

4. **Data Selection and Slicing:**
   - Select specific columns:

   ```python
   df['column_name']
   ```

   - Select rows based on conditions:

   ```python
   df[df['column_name'] > 50]
   ```

5. **Data Visualization:**
   - Create basic visualizations:

   ```python
   import matplotlib.pyplot as plt
   df['column_name'].plot(kind='hist')
   plt.show()
   ```

   - Pair plots for exploring relationships between multiple variables:

   ```python
   import seaborn as sns
   sns.pairplot(df)
   ```

6. **Grouping and Aggregation:**
   - Group data by a column and calculate statistics:

   ```python
   df.groupby('category_column').mean()
   ```

7. **Correlation Analysis:**
   - Compute the correlation matrix:

   ```python
   df.corr()
   ```

8. **Outlier Detection:**
   - Identify outliers using z-scores:

   ```python
   from scipy import stats
   z_scores = np.abs(stats.zscore(df['column_name'])
   ```

9. **Data Transformation:**
   - Apply functions to columns:

   ```python
   df['column_name'] = df['column_name'].apply(function)
   ```

   - Apply transformations (e.g., log transformation):

   ```python
   df['column_name'] = np.log(df['column_name'])
   ```

10. **Categorical Variables:**
    - Get frequency counts of unique values:

    ```python
    df['category_column'].value_counts()
    ```

11. **Data Export:**
    - Save the modified DataFrame to a new file:

    ```python
    df.to_csv('new_data.csv', index=False)
    ```

These are some of the common pandas syntax and functions you can use for EDA. Depending on your specific dataset and analysis goals, you may need to use additional pandas functions and techniques to explore and analyze your data effectively.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

