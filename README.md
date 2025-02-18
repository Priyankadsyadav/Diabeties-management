# Using Machine Learning to predict Blood Glucose

## Motivation

  The main purpose of this project was to use machine learning to predict a patient with type 1 diabetes blood glucose.
Complex models that are used in the industry today have the need to receive many inputs, such as carbs and insulin doses.
Those inputs aren't easy to be handled by the patient and have also a good probability of wrong inserts. With that in mind,
a neural network would receive only the blood glucose values from a Continuous Glucose Monitor(CGM - a sensor that shows blood
glucose values for the patient) and show in the output the next values for 30 minutes, preventing the patient from having
to deal with unexpected hipo or hyperglycemia.


## Why LSTM?

LSTM is a certain type of recurrent neural network that will work really well with time series problems. Most of the recurrent
neural networks deal with the problem of long term dependency problem. With the "forget gate layer", this neural network is
able to keep long term data that still important.

## Datasets

The datasets used in this project were generated from UVA/Pandova Type 1 diabetes simulator implemented in Python that you 
can check [here](https://github.com/jxx123/simglucose).

There were used 4 adolescent patients:
  - Patients 7 and 8 were patients without a good blood glucose time in range.
  - Patient 8 was the one used to train the model
  - Patient 1 was a patient with good blood glucose time in range.
  - Patient 10 was a patient with a medium blood glucose time in range.


## Training and testing


The model is set to receive 20 data points in the past and predict 6 points in the future. Considering the delta between each CGM signal equal to 5 minutes, 
the model is using 100 minutes before to predict 30 minutes ahead. Long carbs usually take around 90 minutes to be ingested and most of the insulins have their peak at 60-90 minutes. With that in mind, the 20 last points were used to predict the next 6.

After training the model with part of patient's 8 data, the resulting model was applied to the rest of the patient 8 data:

#### Patient 08 Test Results - RSME: 15,10

#### Patient 01 Results - RSME: 5,15

#### Patient 10 Results - RSME: 5,82

#### Patient 07 Results - RSME: 15,6


In the end, the model performed really well. The RSME( Root-Square-Mean Error) was the error variable used to evaluate the model's results.




