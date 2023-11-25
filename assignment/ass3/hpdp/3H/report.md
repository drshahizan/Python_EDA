<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 3: Exploratory Data Analysis (EDA) Using Big Data

![Screenshot 2023-11-26 010032](https://github.com/drshahizan/Python_EDA/assets/142320760/ac6072fb-6fef-4eb5-894e-8d7d282ab67c)

### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
|ALIEYA ZAWANIE BINTI A ZAINI       | A21EC0156 | Assignment 3    |
|IZZAT HAQEEMI BIN HAIRUDIN         |  	A21EC0033   |  Assignment 3      |
|NG ZI XING             |A21EC0213   | Assignment 4     |
|MOHAMAD AZRI HADIF BIN MOHAMMAD RIZAL         |  A21EC0054  | Assignment 5      |

# Table of Contents

1. [Dataset Selection](#Selection)
2. [Data Acquisition](#Acquisition)
3. [Setting Up the Environment](#Environment)
4. [Data Preprocessing](#Preprocessing)
5. [Exploratory Data Analysis](#Analysis)
6. [Documentation](#Documentation)

## 1. Dataset Selection <a name="Selection"></a>
<p>The dataset that we chose from kaggle is about emerging mobile money transaction domain where PaySim simulates mobile money transactions based on a sample of real transactions extracted from one month of financial logs from a mobile money service implemented in an African country. The original logs were provided by a multinational company, who is the provider of the mobile financial service which is currently running in more than 14 countries all around the world.</p>

<p>Download The Dataset <a href="https://www.kaggle.com/datasets/ealaxi/paysim1/data">Here</a></p>

### Description
<table>
  <tr>
    <th>Column Name</th>
    <th>Description</th>
  </tr>
      <tr>
    <th>step</th>
    <th>maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).</th>
  </tr>
     <tr>
    <th>type</th>
    <th>Transaction type</th>
  </tr>
  <tr>
    <th>amount</th>
    <th>amount of the transaction in local currency.</th>
  </tr>
  <tr>
    <th>nameOrig</th>
    <th>customer who started the transaction</th>
  </tr>
  <tr>
    <th>oldbalanceOrg</th>
    <th>initial balance before the transaction</th>
  </tr>
  <tr>
    <th>newbalanceOrig</th>
    <th>new balance after the transaction.</th>
  </tr>
  <tr>
    <th>nameDest</th>
    <th>customer who is the recipient of the transaction</th>
  </tr>
  <tr>
    <th>oldbalanceDest</th>
    <th>initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants).</th>

  </tr>
  <tr>
    <th>newbalanceDest</th>
    <th>ew balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants).</th>
  </tr>
  <tr>
    <th>isFraud</th>
    <th>This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.</th>
  </tr>
   <tr>
    <th>isFlaggedFraud</th>
    <th>The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.</th>
  </tr>

</table>

![Screenshot 2023-11-26 011922](https://github.com/drshahizan/Python_EDA/assets/142320760/98264671-4d21-43fc-ae84-9e5d89516e30)

## 2. Dataset Acquisition <a name="Acquisition"></a>
<p>The dataset named "PS_20174392719_1491204439457_log.csv" is in CSV file format which stands for "Comma-Separated Values." It is a simple and widely used text file format for storing tabular data. In a CSV file, each line of the file represents a row of the table, and the values in each row are separated by commas (or another delimiter, such as a semicolon).</p>

## 3. Setting Up the Environment <a name="Environment"></a>
**a) Importing & Install the necessary tools and libraries**.<br>
The libraries used in this assignment are Dask DataFrame, NumPy, Pandas, and the combination of Matplotlib and Seaborn suggests a well-rounded approach to data analysis. Dask and Pandas cater to different scales of data, while NumPy provides efficient numerical operations. Matplotlib and Seaborn enhance your ability to communicate insights visually, making your analysis more comprehensive and accessible.


<br>![image](https://github.com/drshahizan/Python_EDA/assets/142320760/9ccc6bc6-c8ae-4849-9678-0170efbc0fb4)
![Screenshot 2023-11-26 012912](https://github.com/drshahizan/Python_EDA/assets/142320760/d4c83e7d-31bf-41b1-a80f-103f3c37d007)<br>


**b) Importing dataset.** <br>
In this section code, the dataset is directly imported from kaggle where we did not need to download it into our device. In order to use this, we need to download our kaggle API where it is located in the kaggle account section. After running this code, it requires us to insert the kaggle.json which is the kaggle API into the Google Colab file.


<br>![Screenshot 2023-11-26 013627](https://github.com/drshahizan/Python_EDA/assets/142320760/8ba5a04d-d17b-4731-ab86-1c66cecba8d9)<br>

**c) Displaying basic information about the DataFrame.** <br>
To display basic information about the dataset, codes that are used are `'ddf.dtypes'` , `'describe()'` , `'ddf.isnull().sum()'` , `'.head()'` . These are to see display descriptive statistics of numeric columns, check for missing values and display the first few rows of the DataFrame.

<br>![Screenshot 2023-11-26 013942](https://github.com/drshahizan/Python_EDA/assets/142320760/bd4d721b-a9f4-4734-bbf2-474443841b50)<br>
<br>![Screenshot 2023-11-26 014523](https://github.com/drshahizan/Python_EDA/assets/142320760/20b3bab7-9185-4140-97d3-87d194e134b0)<br>
<br>![Screenshot 2023-11-26 014601](https://github.com/drshahizan/Python_EDA/assets/142320760/fed3053b-1586-43ff-880f-6bf0c2c6bd57)<br>
<br>![Screenshot 2023-11-26 014623](https://github.com/drshahizan/Python_EDA/assets/142320760/39fea8fb-4dee-4e3c-8ddd-71a0d36ad5bb)<br>

**d) Defining function for reduing memory usage for analysis.** <br>
In the provided code, a function named reduce_mem_usage_ddf is defined to optimize the memory usage of a Dask DataFrame. The function iterates through each column, and for numeric columns, it reduces precision if possible to minimize memory consumption. It uses information from NumPy (np.iinfo for integers and np.finfo for floats) to determine the allowable range for each data type. Non-numeric columns are converted to the 'category' data type to further save memory. The function prints the initial and optimized memory usage, along with the percentage decrease in memory consumption. This approach is valuable when working with large datasets in a distributed computing environment, enhancing computational efficiency and responsiveness.

<br>![Screenshot 2023-11-26 014846](https://github.com/drshahizan/Python_EDA/assets/142320760/ee797f46-0a1e-4ec0-8323-30c2ebeb2833)<br>
<br>![Screenshot 2023-11-26 015137](https://github.com/drshahizan/Python_EDA/assets/142320760/94e5b526-d7ae-46df-865e-91dcff8548f7)<br>

We can see that the memory usage for the dataset decrease as much as 25.4%

## 4. Data Preprocessing <a name="Preprocessing"></a>
**a) Chunking Data Into Smaller Parts.**<br>
Dask is used to process a potentially large dataset efficiently by reading it in chunks rather than loading the entire dataset into memory at once. The script first prints the current working directory and specifies the path to a CSV file. It checks if the file exists and, if so, defines a chunk size of 100,000 rows. The process_chunk function is designed to calculate type totals, min-max values for the 'amount' variable, and print the first few rows for each chunk. The script then employs Dask's capabilities, reading the CSV file in chunks using dd.read_csv and applying the process_chunk function to each partition with map_partitions. This chunking approach is beneficial for working with datasets that may exceed the available memory, allowing for parallelized and memory-efficient processing of the data.

<br>![Screenshot 2023-11-26 015443](https://github.com/drshahizan/Python_EDA/assets/142320760/fc4b5c3d-c89c-4ccc-831d-4ef44f480a3f)<br>

**b) Removing Null Values.**<br>
<br>![Screenshot 2023-11-26 015713](https://github.com/drshahizan/Python_EDA/assets/142320760/c9f70ae1-5a22-4204-90da-353b93f0801f)<br>

**c) Dropping Duplicate Columns.**<br>
<br>![Screenshot 2023-11-26 015819](https://github.com/drshahizan/Python_EDA/assets/142320760/3c3fe2da-0f5f-4278-8717-e7c793592023)<br>

## 5. Exploratory Data Analysis <a name="Analysis"></a>
**a) Summary Statistics: Compute basic statistics such as mean, median, standard deviation, and quantiles for relevant numerical variables.**

<br>![Screenshot 2023-11-26 020421](https://github.com/drshahizan/Python_EDA/assets/142320760/895ba550-82e7-4da1-b81d-48311f82e778)<br>

**b) Data Visualization: Create visualizations like histograms, box plots, scatter plots, and heatmaps to understand data distributions, correlations, and outliers.**

<br>![Screenshot 2023-11-26 020923](https://github.com/drshahizan/Python_EDA/assets/142320760/a93ad742-8ecb-48b8-8bba-67ae4598bb4c)<br>
<br>![Screenshot 2023-11-26 021141](https://github.com/drshahizan/Python_EDA/assets/142320760/4c84a490-f729-4c69-a049-bc34b8dfa2f0)<br>
<br>![Screenshot 2023-11-26 021221](https://github.com/drshahizan/Python_EDA/assets/142320760/b6cc4e4b-876b-46dc-8dab-38d9764e6e12)<br>
<br>![Screenshot 2023-11-26 021255](https://github.com/drshahizan/Python_EDA/assets/142320760/a92638e7-2fd4-49af-80f2-4338927b7add)<br>
<br>![Screenshot 2023-11-26 021320](https://github.com/drshahizan/Python_EDA/assets/142320760/4db9b94d-3f50-451a-bd48-77906b3de189)<br>

**c) Data Exploration: Explore the dataset's structure and identify any patterns, trends, or anomalies. Pay attention to variables' distributions, relationships, and potential insights.**

<br>![Screenshot 2023-11-26 021457](https://github.com/drshahizan/Python_EDA/assets/142320760/f4c0a0fa-d86e-4d4c-ae52-54962a4f7298)<br>
<br>![Screenshot 2023-11-26 021457](https://github.com/drshahizan/Python_EDA/assets/142320760/f4c0a0fa-d86e-4d4c-ae52-54962a4f7298)<br>
<br>![Screenshot 2023-11-26 021556](https://github.com/drshahizan/Python_EDA/assets/142320760/198e671a-41bd-460f-9803-95ecdc35b530)<br>
<br>![Screenshot 2023-11-26 021727](https://github.com/drshahizan/Python_EDA/assets/142320760/7773f458-e9ed-4403-9b71-6a69dbb5a9dc)<br>
<br>![Screenshot 2023-11-26 021914](https://github.com/drshahizan/Python_EDA/assets/142320760/6515f780-4206-46ed-accb-438de73f32a8)
![Screenshot 2023-11-26 021949](https://github.com/drshahizan/Python_EDA/assets/142320760/52707a7b-0694-489d-ab8e-66ec242e405e)<br>

**d) Feature Engineering: If applicable, create new features or transform existing ones to better support your analysis.** <br>
The code is done by taking the isFraud as the target variable for Mutual Information. The variable taken to prove the relation with "isFraud" is only column with the datatype "int64" or "float64" as the dtype for isFraud is in interger. Therefore, we only have 3 column that have the same dtype. The first thing that is done is by measuring the MI score to see which one is the highest among them all.

Then, we can proceed in doing Feature Generation , Further MI analysis and so on. But in the dataset that we use , the MI score are okay but looking back the highest MI score which is "step" the distinct value of it is only "1". Therefore, it might not be provding diverse information for disinguishing between different instances of the target variable. Not to mention, that the "isFraud" column only have the value "0" and "1". So in conclusion, doing FE in a numerical manner using this dataset might not be the best choice. By doing a categorical FE might produce better result

<br>![Screenshot 2023-11-26 022246](https://github.com/drshahizan/Python_EDA/assets/142320760/24a2b2d7-3620-44d8-9d29-248563963536)<br>

## 6. Documentation <a name="Documentation"></a>
## Conclusion

### Transaction Types:
- The dataset encompasses diverse transaction types, including CASH-IN, CASH-OUT, DEBIT, PAYMENT, and TRANSFER.

### Fraud Distribution:
- Fraudulent transactions are infrequent, constituting approximately 0.13% of the dataset.
- Transactions flagged as fraud are even rarer, with a mean of approximately 0.00000251%.

### Feature Engineering:
- Challenges were encountered in using `mutual_info_classic` for numerical values, primarily due to the target variable ("isFraud") having only one unique value (0), indicating no fraud.
- The limitations of the target variable prompted the need for reassessment of the chosen feature engineering method and exploration of alternatives.
- Consideration of other analysis methods that provide meaningful insights, especially given the constraints of the target variable's unique values.

### Balance Changes:
- Analysis of balance changes for origin and destination accounts revealed negative values indicating a decrease, reflecting outgoing transactions.

In summary, the exploratory data analysis using Dask, Seaborn, and Matplotlib unveiled insights into transaction types, fraud distribution, and balance changes. While facing challenges with the target variable and feature engineering, further refinement and exploration of alternative analysis approaches will enhance the understanding of the dataset, contributing to effective fraud detection strategies.
