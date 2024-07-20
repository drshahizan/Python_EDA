
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise 6: Correlation Analysis

The steps to calculate the correlation matrix using the `corr()` method in pandas and visualize it using a heatmap in Seaborn to identify strongly correlated features in the Titanic dataset.

### Step 1: Load the Titanic Dataset
1. **Load the dataset:**
   ```python
      import pandas as pd
      import seaborn as sns
      import matplotlib.pyplot as plt

      url = 'https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv'
      titanic = pd.read_csv(url)
   ```

### Step 2: Calculate the Correlation Matrix

# Select only numeric columns for correlation calculation
numeric_cols = titanic.select_dtypes(include=['number']).columns
corr_matrix = titanic[numeric_cols].corr()

1. **Select only numeric columns for correlation calculation:**
   ```python
      numeric_cols = titanic.select_dtypes(include=['number']).columns
      corr_matrix = titanic[numeric_cols].corr()
   ```

### Step 3: Visualize the Correlation Matrix Using a Heatmap

2. **Create the heatmap:**
   ```python
      plt.figure(figsize=(10, 8))
      sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', center=0)
      plt.title('Correlation Matrix of Titanic Dataset')
      plt.show()
   ```



### Full Code
Here's the complete code in a single notebook:

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load the Titanic dataset from the provided URL
url = 'https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv'
titanic = pd.read_csv(url)

# Select only numeric columns for correlation calculation
numeric_cols = titanic.select_dtypes(include=['number']).columns
corr_matrix = titanic[numeric_cols].corr()

# Create a heatmap to visualize the correlation matrix
plt.figure(figsize=(10, 8))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', center=0)
plt.title('Correlation Matrix of Titanic Dataset')
plt.show()


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

