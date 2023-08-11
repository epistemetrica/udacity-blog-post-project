# Udacity Data Science Blog Post Project

Adam Wilson, July 2023

## Project Description
This project follows a CRISP-DM process to gain insights from AirBnB rental data in Seattle, WA. The project is graded according to [this rubric](https://review.udacity.com/#!/rubrics/1507/view) and consists of the following parts:
- The [github repository](https://github.com/epistemetrica/udacity-blog-post-project), including the main jupyter notebook and this README.
- A cooresponding [Medium blog post](https://medium.com/@wilson.adamp/price-determinants-in-the-seattle-airbnb-rentals-market-de0ac00b0d81) communicating insights to a non-technical audience. 

## Data

Udacity suggested [Kaggle](https://www.kaggle.com/datasets/airbnb/seattle) as a source for AirBnB rental data; however, the primary source, [Inside AirBnB](http://insideairbnb.com/get-the-data), offered updated data with more observations in the same format, so those data were used.  Their [data assumptions](http://insideairbnb.com/data-assumptions/) and [data dictionary](https://docs.google.com/spreadsheets/d/1iWCNJcSutYqpULSQHlNyGInUvHg2BoUGoNRIGa6Szc4/edit?usp=sharing) provide important information about the nature of the data. 

This data set is from a single AirBnB market - Seattle, WA. 

## Code
The code for this project is written in a Jupyter (v2023.6.1101941928) notebook running a Python 3.11.3 kernel in a virtual environment. 

### Python Libraries
- numpy
- pandas
- scipy
- matplotlib.pyplot
- matplotlib.dates
- seaborn
- [folium](https://python-visualization.github.io/folium/)
- geopandas
    - installation of geopandas can be problematic in some environments; I recommend installing with the conda-forge channel per [these instructions](https://geopandas.org/en/stable/getting_started/install.html) 
- geopy
- KNNImputer from sklearn.impute
- LinearRegression from sklearn.linear_model
- train_test_split from sklearn.model_selection
- r2_score from sklearn.metrics
- [statsmodels.api](https://www.statsmodels.org/stable/install.html)
- het_white from statsmodels.stats.diagnostic 

## Project Motivation

My background is in agricultural economics, and one of my masters thesis advisors specialized in hedonic analyses in housing markets. The AirBnB data lends itself well to this type of study, so I chose to apply a hedonic model to the Seattle AirBnB market to see what can be learned. 

## Files

- apw_airbnb_project.ipynb
    - this is the main Jupyter notebook containing the python code as well as discussion of the CRISP-DM and econometric methods. 
- listings.csv
    - the primary data set, as downloaded from Inside AirBnB
    - the file is fairly large, and thus not hosted on github
- neighbourhoods.geojson
    - the boundary shape files for the various neighbourhoods of Seattle, as downloaded from Inside AirBnB
- regression_model_output.csv
    - a csv of the output tabel for the primary econometric model
- .gitignore
- this README.md

## Results

The regression results gives us insight into the effects of a single variable on price, holding all other variables constanct. We set out to analyze the effects on price of three aspects of AirBnB listings:
- location
- features
- host characteristics

### Location 

In the initial graph of median prices by neighborhood, it seemed that listings in Queen Anne and Downtown commanded higher prices, while renters were willing to pay less for listings in neighborhoods such as Northgate or Interbay. As it turns out, if we hold everything else constant, whether a listing is in Queen Anne or Other Neighbourhoods makes no significant difference. Even more surprising: if a renter could rent an otherwise-equivalent listing in the Other Neighbourhoods, they would be willing to pay significantly less to be in Downtown. Perhaps this is due to Seattle's infamous downtown traffic, or perhaps the average renter simply prefers the quieter parts of town. As for the neighbourhoods with lower median prices, it turns out that whether a listings is in the Interbay area has no effect on prices, but being in Northgate indeed carries a price penalty of 9.6%. It's important to note that this assumes differences in neighbourhood while holding the distance to the city center constant. 

Speaking of, moving a listing further away from the city center carries a significant price penalty, with the first mile reducing price by 11.7%. As expected, this effect is smaller as the distance increases. Since this is a quadratic hedonic model in regards to distance, the hedonic price of distance for listing $i$ is given by $\frac{\partial ln(P_i)}{\partial d_i} = \beta_1 + 2\beta_2 d_i$ where $d_i$ is the distance of listing $i$ from the city center. Using this formula, we can compute that the effect of distance reaches an inflection point of zero effect on price around 8.6 miles from downtown. This is, incidentally, about the maximum distance of any listing in the dataset. 

### Listing Features

Basic intuition dictates that renters are willing to pay higher prices for additional features, and this analysis supports that intuition: almost all of the feature variables have significant positive effects on price. "Entire place" rentals garner 22% higher prices than "Private Rooms" and nearly 50% higher prices than "Shared Rooms." Additional guests bump prices up 15.5%, with the effect decreasing ever-so-slightly as the number of guests gets higher. 

Interestingly, while the number of bedrooms, bathrooms, and beds all have significant positive effects on price, none of their quadratic terms are significant, indicating constant effects for each additional room or bed regardless of the quantity. This is somewhat surprising: since the guest capacity is being held constant, it's hard to imagine what utility renters are getting from additional beds and rooms. The ratio of guest capacity to number of beds in our database has mean 1.98 and a standard deviation of 0.6, so perhaps this is simply due to the relatively tight relationship between the guest capacity and the number of beds and rooms available. 

As expected, buyers are willing to pay higher prices for amenities such as hot tubs, air conditioning (which is more common these days but still not a given&mdash;only about 40% of listings offer it), and EV chargers.

Perhaps the most surprising results is that free parking seems to have a negative effect on prices, albeit with somewhat weak statistical significance. In a city known for its strict and expensive parking enforcement, it is admitedly hard to believe that renters would not be willing to pay a premium for parking. 

The number and quality of reviews (taken as proxies for how nice the rentals actually are) both have significant positive effects on price, although the effect of number of reviews is _remarkably_ tiny at 0.04%. 

### Host Characteristics

Renters are willing to pay a higher price to rent from Superhosts, but don't seem to care whether they can instantly book the rental. Gibbs and collaborators included whether or not a host is a "professional" based on whether the host manages 2 or more listings, and I have done the same for comparison. It is intuitive that professional hosts might perform higher than nonprofessionals and thus renters might be willing to pay higher prices to enjoy this performance. However, when renting a property on AirBnB, how many listings the host manages is generally not observable, so it's hard to imagine it having any practical effect on prices. My analysis supports this view: whether the host is a professional has no significant effect on prices. 

### Limitations of the model

As mentioned at the beginning of this notebook, the data present a fundamental limitation to analyzing price determinants since we only observe _advertised_ prices rather than actual sales prices. There is no way to know from this data if, for example, hosts end up giving discounts or refunds. Cleaning and AirBnB fees are also not observed in this data set, further contributing to the potential differences between the listing price and the actual prices paid by renters. It's quite possible these differences are systematically related to the other variables: perhaps cleaning fees are higher in downtown or for listings with certain amenities, and we would certainly expect higher cleaning fees for listings with higher guest capacities, more bedrooms and bathrooms, etc. 

Taken together, these effects may be the cause of the heteroskedasticity and non-normalality of the model residuals. Estimating robust standard errors dampens the negative impact of these econometric issues on our ability to interpret the results, but there is no substitute for better data. 

## Acknowledgements

As always, I am indebted to the outstanding Stack Exchange and Medium communitities, without whom this project would have been impossible. 

Individual blogs and resources are linked throughout; however, the following deserve special thanks:
- Inside AirBnB for their well-curated and tidy data sets
- Chris Gibbs, Daniel Guttentag, Ulrike Gretzel, Jym Morton, and Alasdair Goodwill for their [excellent paper](https://www.researchgate.net/profile/Daniel-Guttentag/publication/316056041_Pricing_in_the_sharing_economy_a_hedonic_pricing_model_applied_to_Airbnb_listings/links/5ab2bf72aca272171001bfc7/Pricing-in-the-sharing-economy-a-hedonic-pricing-model-applied-to-Airbnb-listings.pdf) analysing AirBnB markets with similar data. 
- _Mostly Harmless Econometrics_ by J.D. Angrist and J-S Pischke
