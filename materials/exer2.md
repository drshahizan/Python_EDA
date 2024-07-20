
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Exercise 2: Loading Data with Pandas

How you obtain the Titanic dataset from Kaggle, post it to Google Colab, then import it into a Pandas DataFrame. The first few rows will be displayed using the `head()` method.

## Option 1: Dataset in Google Colab

### Step 1: Download the Titanic Dataset
1. **Go to Kaggle:**
   - Visit the [Titanic dataset page on Kaggle](https://www.kaggle.com/c/titanic/data).

2. **Download the Dataset:**
   - Click on the "Download All" button to download the dataset as a ZIP file.
   - Extract the ZIP file on your computer to access the `train.csv` file.
   - [File: train.csv](https://github.com/drshahizan/dataset/blob/main/titanic/train.csv)

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
## Option 2: Dataset in Github

Sure! Here are the steps to obtain the Titanic dataset from the provided GitHub link, upload it to Google Colab, and import it into a Pandas DataFrame. We'll then display the first few rows using the `head()` method.

### Step-by-Step Instructions

1. **Open Google Colab:**
   - Go to [Google Colab](https://colab.research.google.com/).

2. **Create a New Notebook:**
   - Click on "File" > "New Notebook".

3. **Import Necessary Libraries:**
   - In the first code cell, import the necessary libraries:
     ```python
     import pandas as pd
     ```

4. **Download the Dataset from GitHub:**
   - In the next code cell, use the following code to download the dataset using `wget`:
     ```python
     !wget https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv -O train.csv
     ```

5. **Load the Dataset into a Pandas DataFrame:**
   - In the next code cell, load the dataset and display the first few rows:
     ```python
     df = pd.read_csv('train.csv')
     df.head()
     ```

### Full Code

Here is the complete code you can use in Google Colab:

```python
# Step 1: Import Necessary Libraries
import pandas as pd

# Step 2: Download the Dataset from GitHub
!wget https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv -O train.csv

# Step 3: Load the Dataset into a Pandas DataFrame
df = pd.read_csv('train.csv')

# Step 4: Display the First Few Rows
df.head()
```

### Detailed Steps in Google Colab

1. **Open Google Colab:**
   - Navigate to [Google Colab](https://colab.research.google.com/).

2. **Create a New Notebook:**
   - Click on "File" > "New Notebook".

3. **Import Necessary Libraries:**
   - In the first code cell, type:
     ```python
     import pandas as pd
     ```
   - Press `Shift + Enter` to run the cell.

4. **Download the Dataset from GitHub:**
   - In the next code cell, type:
     ```python
     !wget https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv -O train.csv
     ```
   - Press `Shift + Enter` to run the cell.

5. **Load the Dataset into a Pandas DataFrame:**
   - In the next code cell, type:
     ```python
     df = pd.read_csv('train.csv')
     df.head()
     ```
   - Press `Shift + Enter` to run the cell and display the first few rows of the dataset.

Following these steps, you will be able to download the Titanic dataset from the provided GitHub link, upload it to Google Colab, and load it into a Pandas DataFrame. The first few rows of the dataset will be displayed using the `head()` method.
By following these steps, you will have successfully downloaded the Titanic dataset, uploaded it to Google Colab, loaded it into a pandas DataFrame, and displayed the first few rows using the `head()` method.


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
