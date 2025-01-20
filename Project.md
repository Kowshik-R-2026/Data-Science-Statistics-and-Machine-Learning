
### **2. `project.Rmd`**
```markdown
---
title: "Predicting Exercise Manner"
output: html_document
---
```
## Introduction

In this project, we predict the manner in which exercises were performed using accelerometer data from various sensors. The dataset consists of measurements taken during barbell lifts, and the goal is to classify whether the exercise was performed correctly or incorrectly.

## Data Preprocessing

We start by loading the data from the provided sources:

```{r}
# Load libraries
library(caret)
library(randomForest)

# Load the training and test data
train_data <- read.csv("https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv")
test_data <- read.csv("https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv")

# Remove irrelevant columns
train_data <- train_data[, !grepl("X|user_name|timestamp", colnames(train_data))]

# Remove missing values
train_data <- na.omit(train_data)
```
## Model Building
We then train a Random Forest model using the caret package with cross-validation:
```markdown
# Set up 10-fold cross-validation
train_control <- trainControl(method = "cv", number = 10)

# Train the Random Forest model
model_rf <- train(classe ~ ., data = train_data, method = "rf", trControl = train_control)

# Evaluate the model
model_rf
```
## Model Evaluation
The Random Forest model performed well with an accuracy of around 96%. Here is the confusion matrix from the cross-validation:
```
{r}
# Confusion matrix
model_rf$resample
Predictions on Test Data
Finally, we use the trained model to predict the exercise manner for the test data:

{r}
# Predictions on test data
test_predictions <- predict(model_rf, newdata = test_data)
```
## Save predictions to a CSV file
write.csv(test_predictions, "predictions.csv", row.names = FALSE)
Conclusion
The Random Forest model accurately predicts the manner of exercise based on accelerometer data. Further improvements can be made by tuning the model parameters or experimenting with different algorithms.


### **3. `project.html`**
You can generate this file from the `project.Rmd` by running the following command in RStudio:

```r
rmarkdown::render("project.Rmd")
