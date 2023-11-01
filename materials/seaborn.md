
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# Seaborn

Seaborn is a Python data visualization library based on Matplotlib, designed for creating informative and attractive statistical graphics. It's particularly well-suited for various aspects of Exploratory Data Analysis (EDA). Here are some common Seaborn syntax and functions suitable for EDA:

1. **Importing Seaborn:**
   - Import Seaborn:

   ```python
   import seaborn as sns
   ```

2. **Setting Aesthetic Parameters:**
   - Set the style and color palette for plots:

   ```python
   sns.set(style="whitegrid", palette="husl")
   ```

3. **Distribution Plots:**
   - Create various distribution plots like histograms and kernel density estimates:

   ```python
   sns.histplot(data, kde=True)
   ```

4. **Pair Plots:**
   - Generate pair plots for visualizing relationships between multiple variables:

   ```python
   sns.pairplot(df, hue='category_column')
   ```

5. **Scatter Plots:**
   - Create scatter plots to explore relationships between two variables:

   ```python
   sns.scatterplot(x='x_column', y='y_column', data=df)
   ```

6. **Box Plots:**
   - Generate box plots to visualize data distributions and outliers:

   ```python
   sns.boxplot(x='category_column', y='value_column', data=df)
   ```

7. **Violin Plots:**
   - Create violin plots for a combination of box plots and kernel density estimation:

   ```python
   sns.violinplot(x='category_column', y='value_column', data=df)
   ```

8. **Heatmaps:**
   - Generate heatmaps to visualize correlation matrices:

   ```python
   sns.heatmap(correlation_matrix, annot=True, cmap="YlGnBu")
   ```

9. **Count Plots:**
   - Create count plots to visualize the distribution of categorical variables:

   ```python
   sns.countplot(x='category_column', data=df)
   ```

10. **PairGrids:**
    - Build custom PairGrids for more control over pair plots:

    ```python
    g = sns.PairGrid(df, hue='category_column')
    g.map_upper(sns.scatterplot)
    g.map_diag(sns.histplot)
    g.map_lower(sns.kdeplot)
    ```

11. **Regression Plots:**
    - Create regression plots to explore linear relationships between variables:

    ```python
    sns.regplot(x='x_column', y='y_column', data=df)
    ```

12. **Customizing Plots:**
    - Customize plots with titles, labels, and other attributes:

    ```python
    plt.title('Plot Title')
    plt.xlabel('X-axis label')
    plt.ylabel('Y-axis label')
    ```

Seaborn is known for its high-level abstractions and aesthetically pleasing visualizations. You can use these Seaborn syntax and functions to create informative and attractive plots for EDA, making it easier to explore and understand your data.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)


