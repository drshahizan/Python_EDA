
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Matplotlib

Matplotlib is a popular Python library for creating various types of plots and charts, which is essential for visualizing data during the Exploratory Data Analysis (EDA) process. Here are some common Matplotlib syntax and functions suitable for EDA:

1. **Importing Matplotlib:**
   - Import Matplotlib's `pyplot` module:

      ```python
      import matplotlib.pyplot as plt
      ```

2. **Basic Plot:**
   - Create a simple line plot:

      ```python
      plt.plot(x, y)
      ```

3. **Scatter Plot:**
   - Create a scatter plot to visualize relationships:

      ```python
      plt.scatter(x, y)
      ```

4. **Bar Chart:**
   - Generate a bar chart for categorical data:

      ```python
      plt.bar(categories, values)
      ```

5. **Histogram:**
   - Create a histogram to visualize data distribution:

      ```python
      plt.hist(data, bins=10)
      ```

6. **Box Plot:**
   - Generate a box plot to display data quartiles and outliers:

      ```python
      plt.boxplot(data)
      ```

7. **Pie Chart:**
   - Create a pie chart to represent data proportions:

      ```python
      plt.pie(sizes, labels=labels, autopct='%1.1f%%')
      ```

8. **Heatmap:**
   - Display a heatmap for correlation matrices:

      ```python
      plt.imshow(correlation_matrix, cmap='coolwarm')
      plt.colorbar()
      ```

9. **Customizing Plots:**
   - Customize plot labels, titles, legends, and colors:

      ```python
      plt.xlabel('X-axis label')
      plt.ylabel('Y-axis label')
      plt.title('Plot Title')
      plt.legend(['Legend 1', 'Legend 2'])
      plt.color='blue'
      ```

10. **Subplots:**
    - Create multiple subplots within a single figure:

       ```python
       plt.subplot(2, 2, 1)  # 2x2 grid, first subplot
       plt.plot(x1, y1)
       plt.subplot(2, 2, 2)  # 2x2 grid, second subplot
       plt.plot(x2, y2)
       ```

11. **Saving Plots:**
    - Save plots as image files (e.g., PNG, SVG):

       ```python
       plt.savefig('plot.png')
       ```

12. **Displaying Plots:**
    - Display the plots in the Jupyter Notebook or Python script:

       ```python
       plt.show()
       ```
## Example

```python
import pandas as pd
import matplotlib.pyplot as plt

# URL of the Titanic dataset
url = 'https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv'

# Load the dataset
titanic_data = pd.read_csv(url)

# Display the first 5 rows
print(titanic_data.head())

# Plotting the distribution of passengers' ages
plt.figure(figsize=(10, 6))
plt.hist(titanic_data['Age'].dropna(), bins=30, edgecolor='k', alpha=0.7)
plt.title('Distribution of Passengers\' Ages')
plt.xlabel('Age')
plt.ylabel('Number of Passengers')
plt.grid(True)
plt.show()

# Plotting the survival rate by gender
survival_by_gender = titanic_data.groupby('Sex')['Survived'].mean()
survival_by_gender.plot(kind='bar', color=['blue', 'pink'], alpha=0.7)
plt.title('Survival Rate by Gender')
plt.xlabel('Gender')
plt.ylabel('Survival Rate')
plt.xticks(rotation=0)
plt.grid(True)
plt.show()

# Plotting the survival rate by class
survival_by_class = titanic_data.groupby('Pclass')['Survived'].mean()
survival_by_class.plot(kind='bar', color='green', alpha=0.7)
plt.title('Survival Rate by Class')
plt.xlabel('Class')
plt.ylabel('Survival Rate')
plt.xticks(rotation=0)
plt.grid(True)
plt.show()
```

Matplotlib offers a wide range of customization and plot types, making it a versatile tool for visualizing and exploring data during the EDA process. You can use these Matplotlib syntax and functions to create various types of plots and gain insights into your dataset.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
