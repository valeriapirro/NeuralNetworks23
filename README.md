# NeuralNetworks23

Prepare a public repository with your code, which should be properly polished and documented. 
Inside the repository, add:

-A README file describing ~~very briefly the method~~ and the instructions to install everything that is needed to run the code.
One notebook containing:
-a description of the method you have implemented (up to 1-2 pages);
-a detailed example of how to use the method and the code (similar to our lab sessions);
-a summary of the main results you have obtained.

-------------
# Estimating Training Data Influence by Tracing Gradient Descent 

https://arxiv.org/abs/2002.08484

This paper formalizes the process of identifying the influence that a training instance has on the prediction performed by the Neural Network on a test instance. In the paper, two different methods are implemented. 

First of all, the influence that the training instance z exerts on a test example z' is defined as the change of loss measured between the prediction made on z' before giving z to the Network and the prediction made on z' after giving z to the Network (rivedere la frase). To apply this principle on the whole dataset, the loss changes have to be accumulated while training is progressing. This application is clearly an ideal one since it lays under the assumption to optimize each sample at a time. It's the first approach analyzed by the research, resulting in: <br> 
<p align="center">
  $TracInIdeal(z, z') = \sum\limits_{\substack{t:z_t \\ =z}} (l(w_t, z) - l(w_{t+1}, z'))$ 
  </p> <br>
It's not a convenient formula to apply though, since as mentioned before it lays under the assumption of step by step optimization during training and also because all the test data points need to be known in that process, making the whole application extremely expensive in terms of computational resources requirements.
The first term of the expression represents the loss measured on the prediction $w_t$ at a timestep previous to the use of z in the training and the second term represents the same but in the timestep following the use of the example z. Both are measured on the prediction made about the training example $z'$ . <br> 

Some intermediate results are then analyzed and proposed to solve the applicability problems in the TracInIdeal formula, resulting in the final expression <br>
<p align = "center">
  $TracInCP(z, z') = \sum\limits_{i = 1}^{k} (\eta_i \nabla l(w_t, z') * l(w_t, z))$ 
  </p> <br>

where the term $k$ represents the checkpoints.

In this project have been applied Self Influence and Proponent approaches on a Regression Model, exploiting the California Housing Prices dataset. 
The dataset contains 20,640 observations on 9 variables: median house value, median income, housing median age, total rooms, total bedrooms, population, households, latitude, and longitude in that same order. The dependent variable is the median house value which is the label. 

-------------
