<h1>Property Listings in Kuala Lumpur</h1>

<p align="center">
  <img src="https://www.asiapropertyhq.com/wp-content/uploads/2018/10/kuala-lumpur-property-for-sale.jpg" />
</p>

This is the tabular result of scraping a property listing website for properties for sale in Kuala Lumpur, Malaysia. Only the overview page was scraped so individual property details are scarce. The dataset is obtained from [Kaggle](https://www.kaggle.com/datasets/dragonduck/property-listings-in-kuala-lumpur) that contains 8 columns with 53884 rows.

We are motivated to do EDA on this dataset because we, ourselves are curious about the insights that can be obtain from this dataset. Since it provides information about the capital city of Malaysia, we are delighted to know more about it especially regarding what influence the price of a property in KL. 

<h2>Prepared by:</h2>
<li>Nur Izzah Mardhiah binti Rashidi A20EC0116</li>
<li>Radin Dafina binti Zulkar Nain A20EC0135</li>

<h2>Submission to:</h2>
Prof. Madya. Ts. Dr. Mohd Shahizan Bin Othman
SECP3133-01

<h2>About Dataset</h2>
<table>
  <tr>
    <th>Columns</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Location</td>
    <td>The neighborhood in which the property is situated.</td>
  </tr>
  <tr>
    <td>Price</td>
    <td>The listed sales price in Malaysian Ringgit (RM).</td>
  </tr>
  <tr>
    <td>Rooms</td>
    <td>The number of listed rooms. The format N+M indicates N full bedrooms and M additional rooms that cannot count as such</td>
  </tr>
  <tr>
    <td>Bathrooms</td>
    <td>The number of bathrooms in the property.</td>
  </tr>
  <tr>
    <td>Car parks</td>
    <td>The number of car parks on the property.</td>
  </tr>
  <tr>
    <td>Property Type</td>
    <td>Malaysian properties may fall in one of several property types depending on their characteristics.</td>
  </tr>
    <tr>
    <td>Size</td>
    <td>The total size of the property. Note that some properties are listed by their land area and others by the built-up size, i.e. the total living space of</td>
  </tr>
    <tr>
    <td>Furnishing</td>
    <td>Whether or not the property comes pre-furnished.</td>
  </tr>
    
</table>

<h2>Inferences and Conclusion</h2>

   1. We could see that most properties which is marketed in this website is located at KLCC through the bar graph. There are several possible reasons from this             including too expensive price that people could not afford or people do not prefer to stay at the center of the city or the properties built are exceeding the         population.
   2. However, we do not think that too high price is the main factor for this to happen. This is because if we observe the bar graph that shows mean price based on         location, properties in Taman Duta will be most expensive, yet Taman Duta is not among the highest number of properties marketed in this website.
   3. Hence, we conclude that there is much more factor influencing the number of properties based on the location in this website. Clearly, not just because of the         price.

> Property price does not mainly influence the number of properties being marketed in a location. 

   1. Next, to compare, land area properties display longer box plot than built-up which means that land area has more dispersed data. Built-ups has median value near       2.5 bathrooms and some values outlies from 5 to 10 bathrooms.
   2. However, for the land area, the median is located slightly higher than built-up which is nearly 5. The maximum value is much higher and less outliers are shown         compared to built-ups.
   
> Hence, the data is realistic as land area commonly have a bigger space for more bathrooms than built-ups.

***In general, this dataset is not enough if we would like to determine what exactly influences the market property price.***
    
    
<h2>References and Future Work</h2>

In the future projects, we would like to search for more dataset and information about the possible factors that affect the property price as well as the reason behind the huge amount of marketed properties in this website.

References:

   1. [Pandas Guide](https://pandas.pydata.org/docs/user_guide/text.html)
   2. [Data Visualization](https://www.analyticsvidhya.com/blog/2021/02/an-intuitive-guide-to-visualization-in-python/)
   3. [Dataset](https://www.kaggle.com/datasets/dragonduck/property-listings-in-kuala-lumpur)
