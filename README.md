# Neural_Network_Charity_Analysis

# Overview
This is a project to build a deep learning model.  The project considered preprocessing of data and design of a neural network.  

Preprocessing is an important step and should consider the type of data and the size of the input dataset.  It is not known beforehand whether the dataset is of a linear or non-linear type, and finding a neural network fit to the dataset starts with a trial-and-error approach.  Fortunately, keras comes with a tuner model to assist in finding an optimal model.  Hyperparameters can explored with keras tuner such as the number of neural network layers, nodes, and activation functions.  Finer analyses searches could also be done such as optimizing the "learning rate" if desired.  

The different approaches for input data coupled with neural network design can be assessed by calculating performance measures.  The measures used in this project were the "loss" and the "accuracy" of the neural network model.

# Results <br>

## Data Preprocessing

* What variable(s) are considered in the target(s) for your model?<br>

  One variable was taken to be the target:  "IS_SUCCESSFUL".<br>

* What variables are considered in the features for your model?<br>

  "APPLICATION_TYPE", "AFFILIATION ", "CLASSIFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS", "ASK_AMT"<br>

* What variable(s) are neither targets nor features, and should be removed from the input data?<br>

  "EIN", "NAME"<br>


## Compiling, training and evaluating the model

* How many neurons, layers, and activation functions did you select for your neural network model and why?<br>

  Based on a keras optimzer function the following were used:<br>
  * first layer:  210 nodes
  * second layer: 10 nodes
  * activation function for first and second layers was "elu"
  * output layer used the "sigmoid" activation function.

* Were you able to achieve the target model performance?<br>
No

* What steps did you take to try to increase model performance?<br>
1. Binning data by categorizing features (rather than gathering features into an "other" category)
 coupled with using pandas get_dummies versus using sklearn OneHotEncoder.
2. Creating a keras tuner optimizer function to identiy layer, nodes,and activaiton functions, and
3. Applying the optimized hyperparameters to a smaller dataset (ie smaller input dimension).

## Summary

  Overall, the results of the deep learning model had a loss near 0.6 and an accuracy near 0.71. <br> 
  
  The results were not sensitive to the input dimension. Simplifying the data by grouping the income amount and the asking amount into categorical data did increase the accuracy a little.<br>
  
  In the analysis, I had recategorized income amount (ie, the column "INC_AMT" above) into categories of zero, small, medium, large or corporate accounts. An easy way to reduce the dataset size would be to discard all of the data that corresponds to a zero income amount.  If this is done, then the analysis would only be looking at the small, medium, large, and corporate accounts, but it will miss out on the data which is labeled zero income amount. In other words, a higher accuracy may be achievable by looking at a subset of the original data.
  
  Another approach to reduce the input dataset size could be to implement unsupervised machine learning. By using principal component analysis, the two largest clusters could be found and matched with the columns of the dataset features. Then all rows of the dataset could be deleted except for those which correspond to the two largest clusters. This approach would retain only the rows which contain most of the dataset information accoring to principal component analysis.

