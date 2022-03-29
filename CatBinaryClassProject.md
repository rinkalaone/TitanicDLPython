# <center> Neural Network Project - Binary Classification with Keras</center>
## <center>A Walk-through of the Project</center>
## <center>by Karine Legrand</center>
### <center>January 2022</center>

### Introduction and Goals:
<br>
We will use the well-known 'Titanic' Dataset to design a Neural Network working as a 'Classifier'.<br> The aim is to take a set of features that will be used to train a model, which in turn, would be able to predict the outcome of our dependent variable, i.e  wether a passenger survived or not. We want to predict the outcome of a Category with just two levels (True/False, Survived/Trepassed, 1/0), hence, we are dealing with a so-called "Binary Classification Problem".<br>We choose to use the 'Keras' framework, built on TensorFlow to implement an simple Hands-On Solution to our Problem.

### Strategy followed to get to our Insights:

We will proceed through these different chronological steps:

#### 1) Data Acquisition and Wrangling

In this section we will load and wrangle the dataset to fix any possible issues with the data.<br>
Data treatments that are specific to the use of Keras, as for instance, integer-formating or one-hot-encoding for categorical values, will be handled together with proper neural network Data formatting, in the Preprocessing section. 

#### 2) Preprocessing for Keras

In this section we will further process our Data so that it becomes "Model-ready" to work with. Different steps need to be taken:
- 1) One hot encode categorical variables
- 2) Setting Features and Labels
- 3) Split our Features and associated Labels Data into 3 Chunks: Training, Validation and Test
- 4) Normalize the Input Data so that the different ranges across the Features's values do not tend to bias the weights of the neurons across the network

#### 3) Building and Training the Model

In this section we will:<br>

- Build the Neural Network with following design: <br>We have 11 Input units (one for each feature), 2 hidden layers, each with 32 neurons and a 'ReLu' activation function, 1 output layer with a single unit, since we predict two levels of a binary class (Survived:1 or zero), and a sigmoid activation function, which outputs a number between 0 and 1<br>

- Compile the Model with appropriate parameters: <br> We use the 'Binary Cross Entropy' as the Loss function wich our Network aims to minimize. This function measures the difference of the computed predicted Label from the true Label, kept in our Test Set.<br>The 'Adaptive Moment Optimizer' (short 'adam') is the algorithm that minimizes the Loss function, by computing its gradient and updates the weights in all layers, by back propagation, at each update step (here after each batch is processed).<br>The 'Accuracy' tells us how good the Model performs at minimizing the Loss during the training, by calculating the proportion of correct predicted Labels (on the Train Set), while the Validation Accuracy checks this Proportion on the Validation Set, that is not used by the Model to correct its weights. It enables the Network to "validate if it's learning in a good way and modify it, if it's not.

- Train the Neural Network:<br>This is the phase where The Neural Network starts running and learning from the Train Set, working a number of samples at each step in separate batches, this repeated 'epochs' number of times. We also provide the Validation Data.

#### 4) Predicting 'new' Labels:
Here we will make use of the Test Set, that our Network does not know about and compare the Predictions obtained (a float number between 0 and 1 which is the Probability of obtaining a value of 1 for the Label Class) with the True Labels.<br>In other words, our Network tells us for each Sample we pass it, in X_test, how likely the Passenger of this sample survived and we then can compare these predicted values with the true Values and see if our Model was right!

#### 5) Interpreting the Results
- Testing our trained Model with unseen Data reveals that we correctly predict about more than 85% of the Labels, which is a satisfying performance<br>
- Looking at the predicted Label values directly, we can see that most predictions are either close to zero or close to 1, which also shows that the Model performs well (If the values were close to the threshold of 0.5, the predictions would not have a strong meaning).

### Conclusion and Limitations

The Deep Learning Approach to gain Insights on the collected Data of the Passengers onboard the 'Titanic Vessel', enables us to build a Model that performs quite good at predicting wether a Passenger did survive the Tragedy or not, based on its Characteristics (Age, Travelling Class, Gender, etc...). In other words this Model could construct a complex function relating the Response Variable to all the Feature variables.
Limitation: the performance of our Model depends on the quantity of data samples available. This Dataset contains less than 1000 samples which is not much to work with. The Results are actually quite satisfying, considering this limitation. The reason is, as we could show with an Exploratory Data Analysis, that the Response is strongly correlated with some features in the Dataset ('Gender' and 'Class of Travelling' for example). A Neural Network let this correlation appear!

