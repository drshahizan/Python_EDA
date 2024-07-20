
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise 2: Loading Data with Pandas

Here's how you obtain the Titanic dataset from Kaggle, post it to Google Colab, then import it into a Pandas DataFrame. The first few rows will be displayed using the `head()` method.


### Step 1: Download the Titanic Dataset
1. **Go to Kaggle:**
   - Visit the [Titanic dataset page on Kaggle](https://www.kaggle.com/c/titanic/data).

2. **Download the Dataset:**
   - Click on the "Download All" button to download the dataset as a ZIP file.
   - Extract the ZIP file on your computer to access the `train.csv` file.

### Step 2: Upload the Dataset to Google Colab
1. **Open Google Colab:**
   - Go to [Google Colab](https://colab.research.google.com/) and create a new notebook if you haven't already.

2. **Upload the File:**
   - In Colab, click on the folder icon on the left sidebar to open the file explorer.
   - Click on the upload icon (a paperclip) at the top of the file explorer.
   - Select the `train.csv` file from your computer and upload it.

### Step 3: Load the Dataset into a pandas DataFrame
1. **Import Required Libraries:**
   - In the first code cell, type the following code to import pandas:
     ```python
     import pandas as pd
     ```

2. **Load the Dataset:**
   - In the next code cell, type the following code to load the dataset into a pandas DataFrame:
     ```python
     df = pd.read_csv('train.csv')
     ```

3. **Display the First Few Rows:**
   - In the next code cell, type the following code to display the first few rows of the DataFrame:
     ```python
     df.head()
     ```

### Full Code
Your final notebook should look like this:

1. **Code Cell 1:**
   ```python
   import pandas as pd
   ```

2. **Code Cell 2:**
   ```python
   df = pd.read_csv('train.csv')
   ```

3. **Code Cell 3:**
   ```python
   df.head()
   ```

### Step-by-Step Execution
1. **Run the first cell to import pandas.** 
   - Click on the cell to select it.
   - Press `Shift + Enter` to run the cell.

2. **Run the second cell to load the dataset.**
   - Click on the cell to select it.
   - Press `Shift + Enter` to run the cell.

3. **Run the third cell to display the first few rows of the DataFrame.**
   - Click on the cell to select it.
   - Press `Shift + Enter` to run the cell.
   - You should see the first few rows of the Titanic dataset displayed as output.

By following these steps, you will have successfully downloaded the Titanic dataset, uploaded it to Google Colab, loaded it into a pandas DataFrame, and displayed the first few rows using the `head()` method.


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

