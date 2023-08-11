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

## Project Criteria

