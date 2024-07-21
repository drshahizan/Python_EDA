
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise: Exploratory Data Analysis (EDA) using SweetViz on the Titanic dataset.

### Step-by-Step Guide to EDA with SweetViz

1. **Install SweetViz**:
   First, you need to install the SweetViz library. You can do this using pip:
   ```bash
   pip install sweetviz
   ```

2. **Import Libraries**:
   Import the necessary libraries, including pandas and sweetviz.
   ```python
   import pandas as pd
   import sweetviz as sv
   ```

3. **Load the Dataset**:
   Load the Titanic dataset from the provided URL.
   ```python
   url = "https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv"
   data = pd.read_csv(url)
   ```

4. **Analyze the Dataset**:
   Use SweetViz to analyze the dataset.
   ```python
   report = sv.analyze(data)
   ```

5. **Generate the HTML Report**:
   Generate an HTML report to visualize the EDA results.
   ```python
   report.show_html('SweetViz_Report.html')
   ```

6. **View the Report**:
   Open the generated `SweetViz_Report.html` file in your web browser to explore the EDA results.

### Full Code Example
Here's the complete code to perform EDA using SweetViz:
```python
import pandas as pd
import sweetviz as sv

# Step 1: Load the dataset from the provided URL
url = "https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv"
data = pd.read_csv(url)

# Step 2: Analyze the dataset using SweetViz
report = sv.analyze(data)

# Step 3: Generate a HTML report
report.show_html('SweetViz_Report.html')

# Print a success message
print("EDA report generated successfully. Check the SweetViz_Report.html file.")
```

By following these steps, you should be able to generate a comprehensive EDA report for the Titanic dataset using SweetViz. 

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)


