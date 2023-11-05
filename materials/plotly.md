
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Plotly

Plotly is a versatile Python library for creating interactive and visually appealing data visualizations. It's particularly well-suited for Exploratory Data Analysis (EDA) when you need interactive plots. Here are some common Plotly syntax and functions suitable for EDA:

1. **Importing Plotly:**
   - Import Plotly and its submodules:

      ```python
      import plotly.express as px
      import plotly.graph_objects as go
      ```

2. **Basic Scatter Plot:**
   - Create a simple scatter plot:

      ```python
      fig = px.scatter(data_frame, x="x_column", y="y_column")
      ```

3. **Line Plot:**
   - Generate a line plot to visualize trends over time or continuous data:

      ```python
      fig = go.Figure(data=go.Scatter(x=x_values, y=y_values, mode='lines'))
      ```

4. **Bar Chart:**
   - Create a bar chart for categorical data:

      ```python
      fig = px.bar(data_frame, x="category_column", y="value_column")
      ```

5. **Histogram:**
   - Generate a histogram for data distribution:

      ```python
      fig = px.histogram(data_frame, x="data_column")
      ```

6. **Box Plot:**
   - Create a box plot to visualize data quartiles and outliers:

      ```python
      fig = px.box(data_frame, x="category_column", y="value_column")
      ```

7. **Heatmap:**
   - Display a heatmap for correlation matrices or other 2D data:

      ```python
      fig = go.Figure(data=go.Heatmap(z=correlation_matrix, x=column_labels, y=column_labels))
      ```

8. **3D Scatter Plot:**
   - Generate interactive 3D scatter plots:

      ```python
      fig = px.scatter_3d(data_frame, x="x_column", y="y_column", z="z_column")
      ```

9. **Sunburst Chart:**
   - Create hierarchical sunburst charts for visualizing hierarchical data:

      ```python
      fig = px.sunburst(data_frame, path=["parent", "child"])
      ```

10. **Customizing Plots:**
    - Customize the appearance of plots with titles, labels, legends, and more:

       ```python
       fig.update_layout(title="Plot Title")
       fig.update_xaxes(title_text="X-axis label")
       fig.update_yaxes(title_text="Y-axis label")
       ```

11. **Subplots:**
    - Create subplots with multiple plots in a single figure:

       ```python
       from plotly.subplots import make_subplots
   
       fig = make_subplots(rows=2, cols=2, subplot_titles=("Subplot 1", "Subplot 2", "Subplot 3", "Subplot 4"))

       fig.add_trace(go.Scatter(x=x1, y=y1), row=1, col=1)
       fig.add_trace(go.Scatter(x=x2, y=y2), row=1, col=2)
       fig.add_trace(go.Scatter(x=x3, y=y3), row=2, col=1)
       fig.add_trace(go.Scatter(x=x4, y=y4), row=2, col=2)
       ```

12. **Interactive Features:**
    - Plotly provides interactivity by default, including zoom, pan, and hover tooltips.


Plotly is an excellent choice for EDA when you need to create interactive and visually engaging plots. You can use these Plotly syntax and functions to explore and present your data in a highly interactive way.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)



