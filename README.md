# Neural Network Charity Analysis

## Overview
The purpose of the Neural Network Charity Analysis was to use the features in the [Alphabet Soup Charity dataset](/Resources/charity_data.csv) to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup. A deep learning model was developed using Python to achieve this goal.

The dataset contained more than 34,000 organizations that had received funding from Alphabet Soup over the years. Within the dataset was a number of columns that capture metadata about each organization, such as the following:
- `EIN` and NAME — Identification columns
- `APPLICATION_TYPE` — Alphabet Soup application type
- `AFFILIATION` — Affiliated sector of industry
- `CLASSIFICATION` — Government organization classification
- `USE_CASE` — Use case for funding
- `ORGANIZATION` — Organization type
- `STATUS` — Active status
- `INCOME_AMT` — Income classification
- `SPECIAL_CONSIDERATIONS` — Special consideration for application
- `ASK_AMT` — Funding amount requested
- `IS_SUCCESSFUL` — Was the money used effectively

## Results

### Data Preprocessing
#### What variable(s) are considered the target(s) for your model?
- The `IS_SUCCESSFUL` variable was considered the target for the model because it indicated whether or not applicants were successful after getting funded by Alphabet Soup.

#### What variable(s) are considered to be the features for your model?
- All of the other variables in the dataset were considered the features of the model because they are factors for the model to consider when determining whether or not applicants were successful after getting funded by Alphabet Soup. These variables included:
    - `APPLICATION_TYPE`
    - `AFFILIATION`
    - `CLASSIFICATION`
    - `USE_CASE`
    - `ORGANIZATION`
    - `STATUS`
    - `INCOME_AMT`
    - `SPECIAL_CONSIDERATIONS`
    - `ASK_AMT`

#### What variable(s) are neither targets nor features, and should be removed from the input data?
- The variables that were neither targetes nor features, and were removed from the input data because they were non-beneficial, were the follow two ID columns:
    - `EIN`
    - `NAME`

### Compiling, Training, and Evaluating the Model
#### How many neurons, layers, and activation functions did you select for your neural network model, and why?
The following number of neurons, layers, and activation functions were used for the neural network model:
- First hidden layer
    - Number of neurons: 80
    - Activation function: relu
- Second hidden layer
    - Number of neurons: 30
    - Activation function: relu
- Third hidden layer
    - Number of neurons: 20
    - Activation function: relu
- Ouput layer
    - Activation function: tanh

A total of 130 neurons were used across three hidden layers because it is a good rule of thumb for a basic neural network to have 2-3 times the amount of neurons in the hidden layer as the number of inputs (in this case, 44). The third hidden layer was added after trial and error demonstrating that the third layer increased the accuracy of the model. The output layer activation function was changed from `sigmoid` to `tanh` after similarly performing trial and error, and obtaining a higher accuracy score with the use of the `tanh` function.

#### Were you able to achieve the target model performance?
- No, I was not able to achieve the target model performance of above 75%.

#### What steps did you take to try and increase model performance?
The follow steps were taken to try and increase model performance:
1. The `ASK_AMT` column was converted from an `int` data type to `string` in order to perform binning since we noticed that the column contained 8747 unique values. The data within the column was binned by replacing values with less than 2500 occurrences with `Other`. After encoding the `ASK_AMT` column with the other categorical variables, the accuracy score increased.
2. A third hidden layer with 20 neurons was added to the neural network model after trial and error of running the model with and without the third hidden layer. It was found that the accuracy score increased with the addition of the third hidden layer. Only 20 neurons were used on the third hidden layer because we didn't want to overfit the model.
3. The activation function of the output layer was changed from `sigmoid` to `tanh`. This change was made in order to perform trial and error on the model to see if the `tanh` activation function would increase the accuracy of the model, which it did.

## Summary
Ultimately, the deep learning model achieved an accuracy score of 0.627, meaning the model was able to correctly identify applicants that would be successful if funded by Alphabet Soup approximately 63% of the time. 

![Accuracy Score](/Resources/accuracy_score.png)

The model did not achieve the goal of above 75% accuracy, and could be improved by implementing a different machine learning model. A machine learning model that could potentially solve this classification problem is a linear regression model. After binning and encoding the `ASK_AMT` column, the dataset contained a full set of encoded columns. With all of the columns being encoded, the model would only have to determine the probability of belonging to one of two groups, making a linear regression model a good option to solve the problem.