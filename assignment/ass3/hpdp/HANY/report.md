![image](https://github.com/drshahizan/Python_EDA/assets/87573002/52a8c97e-d051-44ed-8e33-7caacc329b98)<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Assignment 3: Exploratory Data Analysis using Big Data

### Group Name: HANY
### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | :-------------: |
| LIEW YVONNE            |A21EC0045      | Assignment 3 |
| NADIA SYAFIQAH BINTI ZULKIPLI  | A21EC0098      | Assignment 3 |
| ALYA BALQISS BINTI AZAHAR   |  A21EC0158     | Assignment 4 |
| MUHAMMAD HARITH HAKIM BIN OTHMAN              | A21EC0205     | Assignment 4|

## 📚 Objective 
The objective of this assignment is to perform Exploratory Data Analysis (EDA) on a large dataset using big data tools and techniques. EDA is a critical step in understanding the characteristics of a dataset and uncovering insights that can inform further analysis and decision-making.

## 1. Dataset Selection
Our chosen dataset covers hourly weather data from 623 inmet weathers stations of Brazil.
The dataset that we chose can be retrived through this link [Climate Weather Surface of Brazil - Hourly](https://www.kaggle.com/datasets/PROPPG-PPG/hourly-weather-surface-brazil-southeast-region).

## 2. Data Acquisition
The data is conveniently accessible for processing as it is already formatted in CSV.

## 3. Setting Up the Environment
## Import the necessary libraries
```
import numpy as np
import pandas as pd
import gc
import glob
import os

import random
from sys import getsizeof

import matplotlib.pyplot as plt
import seaborn as sns
```

## Load the Dataset
Here are the methods for directly accessing datasets from Kaggle:

1. Login to your [kaggle.com](www.kaggle.com) account.
2. On the top right of the page, you can see your profile. Click on the profile, you will then see an option to view **Your Profile**, **Settings** and **Sign Out**.
3. Click on the **Settings** button, which is indicated by a gear icon.
<div align="center">
  
![img1](https://github.com/drshahizan/Python_EDA/assets/87573002/a88de648-099c-4ef0-915a-472de81b0147)
  
**Figure 1: Display your Kaggle Account.**
</div>

4. On your account page, scroll down until you see an API section. Click on the **Create New Token** as shown in Figure 2 below.
<div align="center">
  
![img2](https://github.com/drshahizan/Python_EDA/assets/87573002/84ab6dc3-5ff3-4b05-a96b-8ace6019d13c)

**Figure 2: Display your Account Settings.**
</div>

5. You will then be given a JSON file named kaggle.json, which contains the API Key, which is unique to your account and must not be shared.
6. Upload the **kaggle.json** file on Google Drive.
<div align="center">
  
![img3](https://github.com/drshahizan/Python_EDA/assets/87573002/12c1cd3d-b621-43d1-947c-8aa19086f24c)
**Figure 3: Display the uploaded kaggle.json file into Drive.**
</div>

7. After the file have been uploaded, use the following command to mount your drive storage on your new colab notebook:

```
from google.colab import drive
drive.mount('/content/drive')
```
8. You will be requested to grant access to your drive storage by selecting your preferred account.
9. Install the required libraries and run the below script :
```
!pip install -q kaggle
!pip install -q kaggle-cli
```

```
!mkdir -p ~/.kaggle
!cp "/content/drive/MyDrive/kaggle.json" ~/.kaggle/
!cat ~/.kaggle/kaggle.json
!chmod 600 ~/.kaggle/kaggle.json
```
10. To access the dataset, run the following command:
• Copy the link after **dataset** keyword.
<div align="center">
  
![img5](https://github.com/drshahizan/Python_EDA/assets/87573002/dd0da122-262d-4285-bd92-5a545586c7d5)
**Figure 5: Shows the dataset link.**
</div>

```
!kaggle datasets download -d PROPPG-PPG/hourly-weather-surface-brazil-southeast-region
```
• Extract the file contents by using this command:
```
!unzip /content/hourly-weather-surface-brazil-southeast-region.zip
```
## 5. Exploratory Data Analysis

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
