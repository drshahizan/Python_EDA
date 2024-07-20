
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

🌟 Hit star button to save this repo in your profile

# Scikit-learn

Scikit-learn is a popular machine learning library in Python, but it also provides tools for data preprocessing, feature selection, and dimensionality reduction, which are essential for various aspects of Exploratory Data Analysis (EDA). Here are some common scikit-learn syntax and functions suitable for EDA:

1. **Importing Scikit-learn:**
   - Import the necessary scikit-learn modules:

      ```python
      from sklearn.preprocessing import StandardScaler, LabelEncoder
      from sklearn.feature_selection import SelectKBest, chi2
      from sklearn.decomposition import PCA
      ```

2. **Standardization and Scaling:**
   - Standardize or scale your numerical data to have zero mean and unit variance:

      ```python
      scaler = StandardScaler()
      scaled_data = scaler.fit_transform(X)
      ```

3. **Label Encoding:**
   - Encode categorical labels into numerical values:

      ```python
      label_encoder = LabelEncoder()
      encoded_labels = label_encoder.fit_transform(y)
      ```

4. **Feature Selection:**
   - Select the most important features using methods like chi-squared or mutual information:

      ```python
      feature_selector = SelectKBest(score_func=chi2, k=5)
      selected_features = feature_selector.fit_transform(X, y)
      ```

5. **Principal Component Analysis (PCA):**
   - Reduce the dimensionality of your data using PCA:

      ```python
      pca = PCA(n_components=2)
      reduced_data = pca.fit_transform(X)
      ```

6. **Dimensionality Reduction:**
   - Implement other dimensionality reduction techniques such as t-SNE, LLE, or Isomap from scikit-learn's manifold module.

      ```python
      from sklearn.manifold import TSNE
      tsne = TSNE(n_components=2)
      reduced_data = tsne.fit_transform(X)
      ```

7. **Missing Value Handling:**
   - Use imputation techniques to handle missing values. Scikit-learn provides methods like `SimpleImputer` and `KNNImputer`.

      ```python
      from sklearn.impute import SimpleImputer
      imputer = SimpleImputer(strategy='mean')
      X_imputed = imputer.fit_transform(X)
      ```

8. **Data Splitting:**
   - Split the data into training and testing sets for validation and model building:

      ```python
      from sklearn.model_selection import train_test_split
      X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
      ```

9. **Statistical Tests:**
   - Use statistical tests available in scikit-learn, such as `t-test`, `ANOVA`, and `chi-squared test`, to explore relationships and significance of features.

      ```python
      from sklearn.feature_selection import f_classif
      f_values, p_values = f_classif(X, y)
      ```
      
      ```python
      import pandas as pd
      from sklearn.model_selection import train_test_split
      from sklearn.preprocessing import StandardScaler
      from sklearn.linear_model import LogisticRegression
      from sklearn.metrics import accuracy_score

      # URL of the Titanic dataset
      url = 'https://raw.githubusercontent.com/drshahizan/dataset/main/titanic/train.csv'

      # Load the dataset
      titanic_data = pd.read_csv(url)

      # Display the first 5 rows
      print(titanic_data.head())

      # Preprocess the data
      # Fill missing values
      titanic_data['Age'].fillna(titanic_data['Age'].median(), inplace=True)
      titanic_data['Embarked'].fillna(titanic_data['Embarked'].mode()[0], inplace=True)

      # Convert categorical variables to numeric
      titanic_data = pd.get_dummies(titanic_data, columns=['Sex', 'Embarked'], drop_first=True)

      # Drop columns that won't be used
      titanic_data.drop(['Name', 'Ticket', 'Cabin'], axis=1, inplace=True)

      # Define features and target variable
      X = titanic_data.drop('Survived', axis=1)
      y = titanic_data['Survived']

      # Split the data into training and testing sets
      X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

      # Standardize the features
      scaler = StandardScaler()
      X_train = scaler.fit_transform(X_train)
      X_test = scaler.transform(X_test)

      # Train a logistic regression model
      model = LogisticRegression()
      model.fit(X_train, y_train)

      # Make predictions
      y_pred = model.predict(X_test)

      # Evaluate the model
      accuracy = accuracy_score(y_test, y_pred)
      print(f'Accuracy: {accuracy:.2f}')
      ```

Scikit-learn offers a comprehensive set of tools for data preprocessing and dimensionality reduction, which are critical steps in EDA. These functions can help you prepare your data for analysis, visualize it more effectively, and uncover important patterns and relationships between features.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
