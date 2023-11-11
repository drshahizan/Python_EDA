<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Assignment 2: Exploratory Data Analysis

<p align="left">
<img src="https://editor.analyticsvidhya.com/uploads/61798ti2.png"  height="300" />
</p>

An Exploratory Data Analysis (EDA) assignment is a task given to students or data analysts to explore and understand a dataset before performing more advanced statistical or machine learning analyses. EDA is a critical initial step in the data analysis process, and it involves summarizing, visualizing, and making sense of the data to gain insights and identify patterns. Here's a description of what an EDA assignment typically involves:

1. **Data Collection**: The first step in EDA is to obtain the dataset. The dataset may be provided to students, or they may be required to source it from publicly available data repositories or collect their own data.

2. **Data Cleaning**: Before any analysis can begin, students need to clean the data. This involves handling missing values, removing duplicates, and addressing any outliers or anomalies in the data. This step ensures that the data is reliable and ready for analysis.

3. **Data Summary**: Students are usually asked to provide a summary of the dataset, which may include basic statistics such as mean, median, standard deviation, and percentiles for numerical variables. For categorical variables, they may list unique categories and their frequencies.

4. **Data Visualization**: Visualization is a key component of EDA. Students are typically required to create various plots and charts to visualize the data's distribution and relationships. This can include histograms, scatter plots, bar charts, box plots, and more.

5. **Correlation Analysis**: Students may need to explore the relationships between variables in the dataset. They can calculate correlation coefficients to identify potential associations between variables.

6. **Hypothesis Testing**: Some EDA assignments may involve testing hypotheses about the data. Students may need to conduct statistical tests to determine if certain assumptions or hypotheses hold true for the dataset.

7. **Pattern Identification**: EDA often focuses on identifying interesting patterns or trends within the data. Students may be asked to look for clusters, trends, or anomalies that can provide valuable insights.

8. **Narrative and Interpretation**: After conducting the above analyses, students are typically expected to write a narrative that explains their findings and interpretations. They should provide insights into what the data reveals and its potential implications.

9. **Visualization and Reporting**: Students may be asked to create a report or presentation summarizing their EDA process and findings. This report should include clear visualizations and well-structured explanations.

10. **Reproducibility**: EDA assignments often emphasize the importance of reproducibility. Students may be required to document their data cleaning, analysis, and visualization processes in a way that others can replicate their work.

11. **Challenges and Limitations**: Students may also be asked to discuss the challenges they encountered during the EDA process and the limitations of their analysis. This demonstrates critical thinking and a deeper understanding of the data.

EDA assignments are essential for developing data analysis skills and gaining a deeper understanding of a dataset's characteristics. They provide valuable insights that can inform further data-driven decision-making processes.

## 📚 Case Study 1

### Project Description

Your submission will be evaluated using the following criteria:

* Dataset must contain at least 5 columns and 10,000 rows of data
* You must ask and answer at least 10 questions about the dataset
* Your submission must include at least 10 visualizations (graphs)
* Your submission must include explanations using markdown cells, apart from the code.
* Your work must not be plagiarized i.e. copy-pasted from somewhere else.

Follow this step-by-step guide to work on your project.

📖 [**Document template**](../Assignment_EDA.ipynb)

### Step 1: Select a real-world dataset 

- The Malaysian dataset must be used for your case study.
- The dataset is available at:
  * [Portal Data Terbuka Malaysia](https://www.data.gov.my/data/ms_MY/dataset)
  * [Department of Statistics Malaysia](https://open.dosm.gov.my/)
  * [data.world](https://data.world/datasets/malaysia)
  * [Dataportal.asia](https://dataportal.asia/dataset?vocab_economy_names=Malaysia)
  * [knoema](https://knoema.com/atlas/Malaysia/datasets)
  * [The World Bank](https://data.worldbank.org/country/MY)
  * [Dataset Search - Google](https://datasetsearch.research.google.com/)
  * [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets.php)
  * [Kaggle datasets](https://www.kaggle.com/datasets)
  * [Awesome-public-datasets](https://github.com/awesomedata/awesome-public-datasets)
  * [Datahub.io](https://datahub.io/collections)
  * [Earthdata](https://www.earthdata.nasa.gov/)
  * [CERN Open Data Portal](http://opendata.cern.ch/)

### Step 2: Perform data preparation & cleaning

- Load the dataset into a data frame using Pandas
- Explore the number of rows & columns, ranges of values etc.
- Handle missing, incorrect and invalid data
- Perform any additional steps (parsing dates, creating additional columns, merging multiple dataset etc.)

### Step 3: Perform exploratory analysis & visualization

- Compute the mean, sum, range and other interesting statistics for numeric columns
- Explore distributions of numeric columns using histograms etc.
- Explore relationship between columns using scatter plots, bar charts etc.
- Make a note of interesting insights from the exploratory analysis

### Step 4: Ask & answer questions about the data

- Ask at least 10 interesting questions about your dataset
- Answer the questions either by computing the results using Numpy/Pandas or by plotting graphs using Matplotlib/Seaborn
- Create new columns, merge multiple dataset and perform grouping/aggregation wherever necessary
- Wherever you're using a library function from Pandas/Numpy/Matplotlib etc. explain briefly what it does

### Step 5: Summarize your inferences & write a conclusion

- Write a summary of what you've learned from the analysis
- Include interesting insights and graphs from previous sections
- Share ideas for future work on the same topic using other relevant datasets
- Share links to resources you found useful during your analysis

### Step 6: Make a submission

- Upload your notebook to github.

## 📚 Case Study 2: Automated EDA Tools

In this case study, you will study three types of **Automated Exploratory Data Analysis (EDA) Tools**. You are required to choose three such tools and demonstrate how they can be implemented step by step using a **Malaysian dataset**. Additionally, you will summarize the **pros and cons** of the **Automated EDA Tools** used. Here are the instructions to guide you through this case study:

1. **Selecting Automated EDA Tools**:
   - Research and select two different **Automated EDA Tools** that you would like to study. These tools are designed to automate the process of data exploration and visualization.
   - Ensure that the selected tools are suitable for analyzing data from a **Malaysian dataset**.

2. **Malaysian Dataset**:
   - Choose an appropriate **Malaysian dataset** for this case study. It could be related to any domain or topic of your choice (e.g., healthcare, finance, demographics, etc.).

3. **Data Preparation**:
   - Collect and load the **Malaysian dataset** into a format compatible with the selected **EDA tools**.
   - Make sure the data is clean and ready for analysis. Perform data preprocessing tasks if necessary.

4. **Implementation of Automated EDA Tools**:
   - Provide a detailed step-by-step guide for implementing each of the selected **Automated EDA Tools**. Include screenshots and explanations where necessary.
   - Cover the following aspects for each tool:
     <br>a. How to load the dataset into the tool.
     <br>b. How to generate basic statistics and visualizations.
     <br>c. How to explore relationships and patterns in the data.
     <br>d. Any unique features or capabilities of each tool that you find noteworthy.

5. **Pros and Cons Analysis**:
   - After implementing both **EDA tools**, summarize the **pros and cons** of each tool based on your experience and observations. Consider factors such as ease of use, comprehensiveness, visualization capabilities, and any limitations.
   - Include your insights on how each tool performed in the context of the **Malaysian dataset** you chose.

6. **Conclusion**:
   - Conclude your case study by summarizing the key findings and insights from your analysis.
   - Provide recommendations or insights on when each tool may be more suitable or preferable based on the specific needs of EDA projects.

7. **References**:
   - Include a list of references and citations for any sources or documentation you used in your case study.

Ensure that your case study is well-organized, well-documented, and provides a clear understanding of how the selected **Automated EDA Tools** work and their applicability to **Malaysian datasets**. Use clear and concise language to convey your findings and conclusions.

### 2. Team Collaboration
🚀 Form project teams comprising a minimum of three and a maximum of four students. Teamwork is essential for this assignment. Please complete the Google Sheets page with your group information [**here**](https://docs.google.com/spreadsheets/d/1vLDgDAu2ai9rAOIKUfE1xUfTEvK2ikpXJ_1F-Xqtk_c/edit?pli=1#gid=834124190). Please update your group information:

| No | Group |  File | Dataset | EDA Tools 1 | EDA Tools 2 | EDA Tools 3 | 
| -----: |  ------ | :-----: |  ----- |  ----- | ----- | ----- | 
| 0. | Sample  |  <a href="./sample/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | 
| 1. | DEADPOOL |  <a href="https://github.com/drshahizan/Python_EDA/tree/main/assignment/hpdp/DEADPOOL%20" ><img src="../../images/answer.png" width="24px" height="24px" ></a> |[Donations_state.csv](https://raw.githubusercontent.com/MoH-Malaysia/data-darah-public/main/donations_state.csv)| Exploripy | AutoViz | DataPrep |
| 2. | Pergolakan |  <a href="./Pergolakan/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | 1. [Cases by State](https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/cases_state.csv)   2.[Death by State:](https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/deaths_state.csv)   3.[Vaccination by State](https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_state.csv) | sweetViz | QuickDA | Toolc
| 3. |  SYNA |  <a href="./SYNA/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | [Covid-19 Vaccination in School of Malaysia](https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_school.csv) | Autoviz | Pandas-profiling | DataPrep |
| 4. | sheemart |  <a href="./sheemart/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | 
| 5. | KHUCHIN |  <a href="./KHUCHIN/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | [Malaysia: Rainfall Indicators at Subnational Level](https://data.humdata.org/dataset/mys-rainfall-subnational) | dabl | QuickDA | ExploriPy |  
| 6. | BERUK |  <a href="./BERUK/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | [Covid Cases Per State](https://github.com/MoH-Malaysia/covid19-public/blob/main/epidemic/cases_state.csv) | sweetViz | pandas-profiling | D-tale |
| 7. | ATONG |  <a href="https://github.com/drshahizan/Python_EDA/tree/main/assignment/hpdp/ATG" ><img src="../../images/answer.png" width="24px" height="24px" ></a> |[Vaccination by District](https://github.com/MoH-Malaysia/covid19-public/blob/main/vaccination/vax_district.csv) | SweetViz | DataPrep | ExploriPy |
| 8. | 3H |  <a href="./3H/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | [Consumer Price Catcher 2023/1 - 2023/9](https://open.dosm.gov.my/data-catalogue/pricecatcher_pricecatcher_2023-09_preview_0) | AutoViz | SweetViz| Pandas-Profiling |
| 9. | HANY |  <a href="./HANY/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | [Hospital](https://github.com/MoH-Malaysia/covid19-public/blob/main/epidemic/hospital.csv) | Pandas-Profiling | SweetViz | Lux |
| 10. | ByteNav |  <a href="./ByteNav/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | [Vaccination for State in Malaysia](https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_state.csv) | Pandas-Profiling | SweetViz | DataPrep |
| 11. | ZProMax  |  <a href="./ZProMax/readme.md" ><img src="../../images/answer.png" width="24px" height="24px" ></a> | [Flow of patients in/out of Covid-19 Quarantine and Treatment Centres (PKRC), with capacity and utilisation](https://github.com/MoH-Malaysia/covid19-public/blob/main/epidemic/pkrc.csv) | Pandas-Profiling | SweetViz | DataPrep | 
| 12. | CAFE KDSE |  <a href="[https://github.com/drshahizan/Python_EDA/tree/main/assignment/hpdp/ATG]" ><img src="../../images/answer.png" width="24px" height="24px" ></a> |[Covid-19 Demographic High Risk](https://github.com/MoH-Malaysia/covid19-public/blob/main/vaccination/vax_demog_highrisk.csv) | SweetViz | DataTile | Lux |
### 3. Academic Integrity
🚫 Uphold the highest standards of academic integrity. Any candidate suspected of cheating in the assignment will face disciplinary action, which may include suspension or expulsion from the University. Moreover, any materials or devices found to be in violation of examination rules and regulations will be confiscated.

### 4. Submission Requirements
📝 Prepare a comprehensive document that outlines the step-by-step process for creating the case study. 
The deadline for submission is **November 12, 2023, at 5:00 PM**. Late submissions will not be accepted and will be disregarded.

## File and Folder Structure 

You must place your file in the submission folder. Within the [`hpdp/`](https://github.com/drshahizan/Python_EDA/edit/main/assignment/hpdp) folder, create a folder called your group. Name the default file as `readme.md`. You can refer to the [documentation template here](https://github.com/drshahizan/Python_EDA/blob/main/assignment/Assignment_EDA.ipynb). Suggested folder structure for this project:

```html
hpdp/your_group/
├── 📁 case_study1/
│   ├── 📄 readme.md
│   └── 📄 cs1.ipynb
├── 📁 case_study2a/
│   ├── 📄 readme.md
│   └── 📄 cs2a.ipynb
├── 📁 case_study2b/
│   ├── 📄 readme.md
│   └── 📄 cs2b.ipynb
└── 📁 case_study2c/
    ├── 📄 readme.md
    └── 📄 cs2c.ipynb

```
## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.
[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
