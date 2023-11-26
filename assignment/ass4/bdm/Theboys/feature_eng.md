## Feature Engineering of Brooklyn Home Sales, 2003 to 2017
### Team Composition
| Name                             | Matric Number |
|----------------------------------|---------------|
| Pang Chern Hong             |MCS231006      |
| Wu JiaMing             |MCS221033      |
| Liu KaiYuan            |MCS231020      |
| Nian Cong             |MCS231007      |

## Feature selection
This data set has a full 111 columns, a large portion of which are useless. A big simplification can be done by removing duplicate columns. Also there are some coumns refering various map ID or file numbers which supposedly have no impact on any of the predictions made.
The following are the parts we retain and their meanings:

Address: The street address of the property.

Apartment Number: Self-explanatory. List the apartment number of the property.

Zip Code: Postal code for the property. Brooklyn has 52 different zip codes, and zip codes have a strong correlation with property value.

Land Sqft: The amount of usable square footage for the property.

Year Built: The year that the property was built.

Building Class At Sale: Building classifications in NYC denote the general condition of a commercial property and indicate the quality of its location and amenities. The building class can significantly impact the property's price, so it will not be dropped.

Sales Price: The final price of the property at the time of sale.

Sale Date: The full date of the property at the time of sale.

School District: The community school district designated for this property.

Prox Code: The proximity code for the property details the attachedness of this property to other properties. It originates from New York City's Department of Planning open data. The values are as follows: 0: Not available, 1: Detached, 2: Semi-attached, 3: Attached.

Lot Area: Lot area represents the size of the piece of land where a property is situated. If the shape of the lot is regular, such as a square, finding the size is as simple as length * width. NYC has many irregular lots that can make finding the area more challenging. Note: Condos will have a lot area of 0.

We will drop all other features past this point to prevent overfitting. Many of the other features have unique properties that would require in-depth solutions to appraise properly. For example, easements can significantly impact the value of a property because easements are usually related to shared driveways, and parking is such a premium in NYC. However, evaluating the easement would require its own set of data and analysis functions.

## Zip code handling
We can see that zip codes in Brooklyn start at 11201 and end at 11256 from the map of brooklyn.

## Outlier for NYC building classess

Searching for Outliers: Building Classes

Each piece of NYC real estate has a building code that dictates what type of real estate it is. Building codes are used for tax and appraisal purposes.

NYC is complicated because people sometimes live in mixed-use real estate.

We can remove further building classes from our dataset by removing classes that are not residential real estate.

NYC publishes a full-list of building codes here. Using their list, we can see that building codes E,F,G,H,I,J,M,M,O,P,Q,T,U,W,Y and Z do not represent residential or mixed-use buildings and instead represent warehouses, factories, government buildings, etc.

We can use Seaborn's countplot() to graph what building classes are in the dataset to find out what we can do to remove outliers further.

## Mutual Information
By definition,  the mutual information of two random variables is a measure of the mutual dependence between the two variables. In our case, we compare the selected features to the sale price, we used the coding from sklearn and seaborn to calculate the mutual information and visualize them.

## PCA 
Principal component analysis is a statistical procedure that allow us to get the certain components that composed of various of features that possess a big part of the affection to the thing we want to estimate. In this project we use PCA to find the most important features in the dataset and then we plot a diagram by using the seaborn to observe the outliers in these PCA components.

## Regression and R-squared
Next, we have to have some way of checking to see how well the linear regression model fits the data. We can use R-squared as a simple way of evaluating the model.

R-squared is a percentage in variance in the independent variable that the dependent variables collectively explain.

R-squared measures goodness-of-fit for a prediction model using a standardized scale.

Scikit-learn includes the r2_score function that generates an R-squared score for our model based on two values, y_test and y_pred. Y_test represents the true sale_price data from our data set, and y_pred represents the predicted sale_price values using our prediction model.

After we generate an R-squared score, we can use Seaborn to generate a regression plot for the data.

## Evaluating our Model: Getting the Root Mean Square Error
While R-squared measures goodness-of-fit, root mean square error, also known as RMSE, measures how accurate the predictions are. It does this by measuring the average difference between the model's predicted values and the actual values.

RMSE is similar to mean squared error, but because the errors, the difference between the predicted values and the actual values, are squared before they are average, RMSE gives high weight to larger errors. Essentialy. RMSE punishes inaccuracy more making innacurate prediction models more obvious.

Before we can generate the RMSE for our mnodel, we need a baseline value to compare it too. We can use the mean of the test data as a naive model to pass into the RMSE function. The RMSE of the machine learning model should be better than just picking the average each time for a prediction.

Scikit-learn can generate RMSE for the model as part of the sklearn.metrics package.

## all these results are ready in our colab file in this folder.
