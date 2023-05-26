# Neural-Network-Analysis-of-Corporate-Funding-Allocation

##Descript
Analysis of over 34,000 businesses that received funding, in order to generate an algorithm to predict effective allocation of funding.

##Overview of the analysis:
The purpose of this analysis was to examine a dataset of 34,000 businesses which had received funding from AlphabetSoupCharity, and to generate a Neural Networking model to predict whether a company would use their funding effectively based on information that is available at the time that funding was allocated. This model would then enable analysis of prospective funding recipients in the future. The goal is to generate a model that has 75% or greater accuracy.


##Data Overview

###Target Variable:
IS_SUCCESSFUL—Was the money used effectively

###Feature Variable:
APPLICATION_TYPE—Alphabet Soup application type
AFFILIATION—Affiliated sector of industry
CLASSIFICATION—Government organization classification
USE_CASE—Use case for funding
ORGANIZATION—Organization type
STATUS—Active status
INCOME_AMT—Income classification
SPECIAL_CONSIDERATIONS—Special considerations for application
ASK_AMT—Funding amount requested

###Irrelevent Variables: (which are removed before model construction)
EIN—Identification column
NAME—Identification column

##Data Preprocessing

-Eliminating EIN and NAME variables.
-Determine which remaining variables have more than 10 values to allow for targeted binning.
-APPLICATION_TYPE, CLASSIFICATION, and ASK_AMT all have more than 10 distinct values, but ASK_AMT is numerical and so does not require binning.
-Bin APPLICATION_TYPE and CLASSIFICATION based on a subjective threshold of 500.
-Convert categorical data to numeric data using pd.get_dummies
-Separate Target Variable array from Feature Variables array in X and y variables.
-Scale data using StandardScaler

##Model Construction

###Compiling
-Define a Neural Network model with prescribed shape of 80 Neurons in the first hidden layer, 30 Neurons in the second hidden layer, and 1 Neuron in the output layer.
-The first two activation functions were defined as 'relu' with the output layer having the activation of 'sigmoid'
-Compile the model and have it output accuracy metric.

###Training
-Train model with X_train_scaled and y_train data over the course of 100 epochs.

###Evaluating
-Evaluate the model accuracy. It showed an accuracy of 72.75% accuracy. This is below our target accuracy.

##Increasing Model Performance (accuracy)

###Attempt 1
-Drop STATUS in addition to EIN and Name variables during preprocessing.
-Decrease threshold for binning from 500 to 100
-Accuracy improved incredibly slightly to 72.76%

###Attempt 2
-Added neurons to the first and second hidden layers. (first: 80 to 90, second: 30 to 50)
-Added a third hidden layer with 20 neurons.
-Accuracy increased to 72.82%

###Attempt 3
-Used sigmoid activation function for all layers instead of relu for the first two and sigmoid for the last.
-Increased epochs from 100 to 150.
-Accuracy decreased to 72.68%

Attempt 4
-!pip install keras-tuner
-Use keras-tuner to create a sequential model with hyperparameter options
-Use 10 steps
-Use max of 50 epochs
-Use between 1 and 100 neurons
-Use relu, tanh or sigmoid
-Use between 1 and 5 layers
-Optimize for value accuracy

-Out of 180 models tested, the optimal one had an accuracy of 73.55% which is the most accurate model of the four, even though it did not achieve the goal of 75%.
-Save this model to a .h5 document.

Project Summary:
-Overall, we tested 5 Neural Network methods and distinct 184 models.
-The most accurate model was generated using the keras-tuner, but only achieved 73.55% accuracy which is below our goal.

-To improve our ability to generate a more accurate classification model, we would recommend adding additional Features focused on organizational success. Additional feature variables might include whether past funding was used effectively, the organization size (employee count or total capital), level of need, organizational age, and CEO years of relevent experience.
-In generating the model, keras-tuner might be used with a larger range of options to explore such as more neurons, more layers, more epochs, or more steps.

