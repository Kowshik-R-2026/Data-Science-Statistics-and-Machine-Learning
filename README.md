# Predicting Exercise Manner using Accelerometer Data

## Introduction

This project involves predicting the manner in which exercises were performed using accelerometer data from wearable devices like Jawbone Up, Nike FuelBand, and Fitbit. The goal is to classify the exercise manner (represented by the variable `classe`) based on various sensor readings.

## Files

- `project.Rmd`: R Markdown file with the project analysis and model building process.
- `project.html`: Compiled HTML report generated from `project.Rmd`.
- `predictions.csv`: CSV file containing the predictions made by the model for the test data.

## Process

1. **Data Preprocessing**: Cleaned the dataset by removing irrelevant columns and handling missing data.
2. **Modeling**: Built a Random Forest model to predict the exercise manner using accelerometer data.
3. **Cross-validation**: Used 10-fold cross-validation to evaluate the model's performance.
4. **Predictions**: Made predictions for 20 test cases and submitted them in the required format.

## Installation

To reproduce this analysis locally, you'll need R and the following R packages:

- `caret`
- `randomForest`
- `pgmm`
- `ElemStatLearn`

Install them using:

```R
install.packages(c("caret", "randomForest", "pgmm", "ElemStatLearn"))
