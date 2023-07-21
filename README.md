# Udacity Data Science Blog Post Project

Adam Wilson, July 2023

## Project Description
This project follows a CRISP-DM process to gain insights from AirBnB rental data in Seattle, WA. The project is graded according to [this rubric](https://review.udacity.com/#!/rubrics/1507/view) and consists of the following parts:
- This [repository](https://github.com/epistemetrica/udacity-blog-post-project), including the main jupyter notebook and this README.
- A cooresponding [Medium blog post]() communicating insights to a non-technical audience. 

## Data

Udacity suggested [Kaggle](https://www.kaggle.com/datasets/airbnb/seattle) as a source for AirBnB rental data; however, the primary source, [Inside AirBnB](http://insideairbnb.com/get-the-data), offered updated data with more observations in the same format, so those data were used.  Their [data assumptions](http://insideairbnb.com/data-assumptions/) and [data dictionary](https://docs.google.com/spreadsheets/d/1iWCNJcSutYqpULSQHlNyGInUvHg2BoUGoNRIGa6Szc4/edit?usp=sharing) provide important information about the nature of the data. 

This data set is from a single AirBnB market - Seattle, WA. 

## Code
The code for this project is written in a Jupyter (v2023.6.1101941928) notebook running a Python 3.9.16 kernel. 

### Python Libraries
- numpy
- pandas
- matplotlib

## Project Criteria

### CRISP-DM Process
#### Business Understanding

How can sellers maximize profits? How can buyers maximize the value they receive for their dollar? Two answer either, and ideally both, of these fundamental questions, we need to examine the following:
- What factors influence price?
- How likely (and how often) is a listing to sell at the asking price?

#### Data Understanding

These data are scraped from AirBnB's website, and thus are inherently marketing data&mdash;they do not contain actual records of sales. This is a significant limitation, as all we observe are _asking_ prices rather than sales prices (for example, we do not observe whether any discounts, refunds or price corrections were issued). We also do not observe whether or not the listing sold, only when it is available for booking in the future (we do not observe whether a listing is unavailable because it has been booked or if the host has blocked the dates). 


#### Data Preparation
#### Data Modeling
#### Result Evaluation
#### Deployment 
