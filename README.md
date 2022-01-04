# Lab2 - Concrete compressive strength regression

## Goal

The goal of this lab is to become familiar a regression workflow by training models to predict concrete strength \[MPa\] based on concrete mixture information using the yellowbrick concrete dataset.

You will try and compare your results to priviously reported models (see Background below):
- Polynomial regression: training RMS=3.96 MPa 􏰀(R2 = 0.890); testing RMS=8.82 MPa (􏰀R2 = 0.791)􏰁 
- Neural network: training RMS=3.01 MPa (􏰀R2 = 0.940);􏰁 testing RMS=4.32 MPa 􏰀(R2 = 0.929)

**Assumption:** We are assuming that the yellowbrick dataset was used in the reference article and that 20% of the data served as the test set.

Models will be trained to minimize root-mean squared error (RMS), as in the reference article. Note that sklearn works with *maximization* and it is custom to *maximize* the *negative* RMS.

## Background
The yellowbrick concrete dataset originates from UCI and was referenced to the following publication:
>Yeh, I-Cheng. 2006. “Analysis of Strength of Concrete Using Design of Experiments and Neural Networks.” Journal of Materials in Civil Engineering 18 (4): 597–604. https://doi.org/10.1061/(ASCE)0899-1561(2006)18:4(597).

In this article, a polynomial regression model was found to be inadequate for strength prediction:
>The results of the compressive strength tests were subjected to polynomial regression using a computer program. Various poly- nomials were tried to represent the measured compressive strength data for seven component contents at a specific age. The best fit for the compressive strength was obtained with a root- mean-square 􏰀RMS􏰁 error of 3.96 MPa 􏰀R2 = 0.890􏰁 and 8.82 MPa 􏰀R2 = 0.791􏰁 for the training data and testing data, respectively. Predictions of the strength of concrete using regressions for the training data and testing data are shown in Figs. 2 and 3, respec- tively. It can be seen that, although the RMS error for the training data is rather low, the RMS error for the testing data is so high as to provide inaccurate predictions. In other words, the model is lacking in generalization.

A neural network is proposed achieving better performance:
>After a number of trials, the best network architecture and parameters that minimize the RMS error of the testing data were selected as follows:
• Number of hidden layers=1; 
• Number of hidden units=4; 
• Learning rate=1.0; and
• Learning cycle=3,000.
Training time on a personal computer was less than 30 s. The RMS error was 3.01 MPa 􏰀R2 = 0.940􏰁 and 4.32 MPa 􏰀R2 = 0.929􏰁 for training data and testing data, respectively. Pre- dictions of the strength of concrete using the network for training data and testing data are shown in Figs. 4 and 5, respectively. Comparing Figs. 5 and 3 , it may be seen that the model obtained by neural networks more accurately predicts the experimental re- sults for the testing data in the range of concrete strength in this study.

We are going to apply our skills and compare our results to the polynomial regression model and neural network.

## What to do

### Datasets
yellowbrick concrete  
https://www.scikit-yb.org/en/latest/api/datasets/concrete.html


### Regressors
- `LinearRegression()`
- `RandomForestRegressor(random_state=64)` 
- `GradientBoostingRegressor(random_state=79)`

### Steps

1. Load data.
2. Inspect data with pandas and seaborn as directed
3. Create training and test sets with `train_test_split()`, `random_state=37`, `test_size=0.2`
4. Compare regression models using cross-validation.
5. Find a better model.
6. Retrain the better model on all training data.
7. Evaluate the better model on test data including prediction-actual and residual plots.

Optional: Use grid search to find an even better model (see Appendix in notebook)

### Specifications
Write the following functions: 
- `get_regressor_neg_rms()`

Function header and documentation are included in `lab2.ipynb`. Implement the function body accordingly.

Use this function to implement the tasks as directed.

### Questions
In this lab, questions appear in each of the steps. 

Use your results to justify/motivate your answers.

## What to hand in
- In the Jupyter notebook `lab2.ipynb` implement the steps above as indicated. 
- Keep code clean and remove any unnecessary cells. 
- Use the results obtained to answer questions throughout the notebook.
- In a section *Reflection*, include a sentence or two about what you liked/disliked, found interesting/confusing/challangeing/motivating while working on this assignment.

During development, checkin progress with git and use descriptive commit messages.
