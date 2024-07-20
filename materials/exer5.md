
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise 5: Data Visualization with Matplotlib and Seaborn

The steps to create various plots such as histograms, box plots, and scatter plots using Matplotlib and Seaborn. We'll visualize the distribution of ages in the Titanic dataset and explore relationships between different features.

### Step 1: Import Necessary Libraries
1. **Import Matplotlib and Seaborn:**
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns
   ```

### Step 2: Load the Titanic Dataset
1. **Load the dataset:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

### Step 3: Create a Histogram for Age Distribution
1. **Histogram:**
   ```python
   plt.figure(figsize=(10, 6))
   sns.histplot(df['Age'].dropna(), kde=True)
   plt.title('Age Distribution')
   plt.xlabel('Age')
   plt.ylabel('Frequency')
   plt.show()
   ```

### Step 4: Create a Box Plot for Age Distribution by Survived
1. **Box Plot:**
   ```python
   plt.figure(figsize=(10, 6))
   sns.boxplot(x='Survived', y='Age', data=df)
   plt.title('Age Distribution by Survival')
   plt.xlabel('Survived')
   plt.ylabel('Age')
   plt.show()
   ```

### Step 5: Create a Scatter Plot for Age vs Fare
1. **Scatter Plot:**
   ```python
   plt.figure(figsize=(10, 6))
   sns.scatterplot(x='Age', y='Fare', data=df)
   plt.title('Age vs Fare')
   plt.xlabel('Age')
   plt.ylabel('Fare')
   plt.show()
   ```

### Step-by-Step Execution

1. **Import Necessary Libraries:**
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns
   ```

2. **Load the Titanic Dataset:**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

3. **Create a Histogram for Age Distribution:**
   ```python
   plt.figure(figsize=(10, 6))
   sns.histplot(df['Age'].dropna(), kde=True)
   plt.title('Age Distribution')
   plt.xlabel('Age')
   plt.ylabel('Frequency')
   plt.show()
   ```

4. **Create a Box Plot for Age Distribution by Survived:**
   ```python
   plt.figure(figsize=(10, 6))
   sns.boxplot(x='Survived', y='Age', data=df)
   plt.title('Age Distribution by Survival')
   plt.xlabel('Survived')
   plt.ylabel('Age')
   plt.show()
   ```

5. **Create a Scatter Plot for Age vs Fare:**
   ```python
   plt.figure(figsize=(10, 6))
   sns.scatterplot(x='Age', y='Fare', data=df)
   plt.title('Age vs Fare')
   plt.xlabel('Age')
   plt.ylabel('Fare')
   plt.show()
   ```

### Full Code
Here's the complete code in a single notebook:

1. **Code Cell 1: Import Necessary Libraries**
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns
   ```

2. **Code Cell 2: Load the Titanic Dataset**
   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

3. **Code Cell 3: Create a Histogram for Age Distribution**
   ```python
   plt.figure(figsize=(10, 6))
   sns.histplot(df['Age'].dropna(), kde=True)
   plt.title('Age Distribution')
   plt.xlabel('Age')
   plt.ylabel('Frequency')
   plt.show()
   ```

4. **Code Cell 4: Create a Box Plot for Age Distribution by Survived**
   ```python
   plt.figure(figsize=(10, 6))
   sns.boxplot(x='Survived', y='Age', data=df)
   plt.title('Age Distribution by Survival')
   plt.xlabel('Survived')
   plt.ylabel('Age')
   plt.show()
   ```

5. **Code Cell 5: Create a Scatter Plot for Age vs Fare**
   ```python
   plt.figure(figsize=(10, 6))
   sns.scatterplot(x='Age', y='Fare', data=df)
   plt.title('Age vs Fare')
   plt.xlabel('Age')
   plt.ylabel('Fare')
   plt.show()
   ```


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

