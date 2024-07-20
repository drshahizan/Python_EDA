
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
   !wget https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv -O train.csv
   df = pd.read_csv('train.csv')
   ```

### Step 2: Calculate the Correlation Matrix
1. **Calculate the correlation matrix:**
   ```python
   correlation_matrix = df.corr()
   print(correlation_matrix)
   ```

### Step 3: Visualize the Correlation Matrix Using a Heatmap
1. **Import Seaborn and Matplotlib:**
   ```python
   import seaborn as sns
   import matplotlib.pyplot as plt
   ```

2. **Create the heatmap:**
   ```python
   plt.figure(figsize=(10, 8))
   sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', linewidths=0.5)
   plt.title('Correlation Matrix Heatmap')
   plt.show()
   ```

### Step-by-Step Execution

1. **Load the Titanic Dataset:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Calculate the Correlation Matrix:**
   ```python
   correlation_matrix = df.corr()
   print(correlation_matrix)
   ```

3. **Import Seaborn and Matplotlib:**
   ```python
   import seaborn as sns
   import matplotlib.pyplot as plt
   ```

4. **Create the Heatmap:**
   ```python
   plt.figure(figsize=(10, 8))
   sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', linewidths=0.5)
   plt.title('Correlation Matrix Heatmap')
   plt.show()
   ```

### Full Code
Here's the complete code in a single notebook:

1. **Code Cell 1: Load the Titanic Dataset**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Code Cell 2: Calculate the Correlation Matrix**
   ```python
   correlation_matrix = df.corr()
   print(correlation_matrix)
   ```

3. **Code Cell 3: Import Seaborn and Matplotlib**
   ```python
   import seaborn as sns
   import matplotlib.pyplot as plt
   ```

4. **Code Cell 4: Create the Heatmap**
   ```python
   plt.figure(figsize=(10, 8))
   sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', linewidths=0.5)
   plt.title('Correlation Matrix Heatmap')
   plt.show()
   ```

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

