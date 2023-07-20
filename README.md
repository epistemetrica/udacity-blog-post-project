# Udacity Data Science Blog Post Project

Adam Wilson, July 2023

## Project Description
This project follows a CRISP-DM process to gain insights from AirBnB rental data in Seattle. The project is graded according to [this rubric](https://review.udacity.com/#!/rubrics/1507/view) and consists of the following parts:
- This [repository](https://github.com/epistemetrica/udacity-blog-post-project), including the main jupyter notebook and this README.
- A cooresponding [Medium blog post]() communicating insights to a non-technical audience. 

## Data
Udacity suggested [Kaggle](https://www.kaggle.com/datasets/airbnb/seattle) as a source for AirBnB rental data; however, the primary source, [Inside AirBnB](http://insideairbnb.com/get-the-data), offered updated data with more observations in the same format, so those data were used.

## Code
The code for this project is written in a Jupyter (v2023.6.1101941928) notebook running a Python 3.9.16 kernel. 

### Python Libraries
- numpy
- pandas
- matplotlib

## Project Criteria

### CRISP-DM Process
#### Business Understanding

Questions:
- What factors influence price?
    - Sales data are not included in this set, so we will look at which factors influence _asking_ prices.
- What factors influence total revenue?
    - Common sense dictates that reviews from previous renters impact future sales
    - Since whether a listing is booked is not captured in these data, we will try to predict reviews based on advertised features


#### Data Understanding
#### Data Preparation
#### Data Modeling
#### Result Evaluation
#### Deployment 
