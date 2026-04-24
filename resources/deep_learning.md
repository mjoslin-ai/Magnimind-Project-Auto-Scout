# Magnimind

Deep Learning


## Layers
There are three types of layers:

* Input layer: raw data that feeds first hidden layer

* Hidden layer: connects input to output layer and is considered deep with many hidden layers

* Output layer: last layer of a neural network model and number of neurons depends on the problem. If regression, usually a single neuron, if classification, depends on number of classes. 


## Neuron
Each layer is made up of neurons or perceptrons and perform two operations: 

* Aggregation: multiplies and sums incoming inputs with weights 

* Activation: applies a specified activation function to obtained results

$$
\text{Activation\_fn}(y) = \text{Activation\_fn}\left(b + x_1 \cdot w_1 + x_2 \cdot w_2 + \dots + x_n \cdot w_n\right)
$$


## Best Hyperparameters
The number of layers and the number of neurons in each layer are hyperparameters to be determined by Backpropagation and Gradient Descent.


## Models
Three most widely-used deep learning architectures

### Convolutional Neural Networks (CNN)
Four primary steps in CNN design:

* Convolution: First stage where input signal (such as an image) is received and uses filters to perform feature extraction.

* Subsampling: Inputs received from the convolution layer are smoothened to reduce the sensitivity of the filters to noise or any other variation

* Activation: Controls how the signal flows from one layer to the other

* Fully connected: All the layers of the network are connected with every neuron from a preceding layer to the neurons from the subsequent layer

* Advantages: Very good for visual recognition

* Disadvantages: Highly dependent on the size and quality of the training data and highly susceptible to noise

### Recurrent Neural Networks (RNN)
Designed for sequential data where the order of information matters (e.g., NLP, speech synthesis, and translation)

Advantages
* Parameter Sharing: Uses the same weights and biases across all time steps, reducing the total number of parameters compared to traditional networks.

* Multimodal Flexibility: Can be combined with CNNs for tasks like image captioning (generating text descriptions for visual data).

Disadvantages:
* Vanishing Gradient Problem: Difficulty tracking long-term dependencies

* Depth Limitations: Cannot be stacked into very deep architectures because the activation functions lead to gradient instability over multiple layers.

### Autoencoders
An unsupervised learning technique that applies backpropagation to reconstruct its input.

Functionally similar to Principal Component Analysis but offers more flexibility and can capture non-linear relationships.

Types
* Vanilla: The simplest version; a neural network featuring just one hidden layer.

* Multilayer: An extension of the vanilla model that incorporates multiple hidden layers for complex data.

* Convolutional: Replaces fully-connected layers with convolutions; ideal for spatial data like images.

* Regularized: Uses a specialized loss function to encourage specific model properties beyond simple input copying.


## Activation Functions
They map a single value to another value and adds non-linearity to deep learning models.

Types of activation functions:

### Sigmoid: 
* mimics the activation in biological brain

* non-zero centered 

* suffers from vanishing gradient from large from large input values

### Hyperbolic tangent (tanh):
* It's zero centered as opposed to sigmoid.

* It also saturates and results in vanishing gradient problem.

### Rectified linear units (ReLU):
* cuts off values below zero

* non-saturating

* converges faster than sigmoid and tanh

* If learning rate set too high, as much as 40% of the neurons can die

### Leaky ReLU:
* proposed to solve dying neurons problem

* Usually the slope for the negative values is set to 0.1

* similar to parametric ReLU (PReLU) where the slope of the negative part is a parameter to learn

### Softmax:
* It's mostly used in output layer.

* Its outputs can be read as the probabilities.


## Loss Functions
Its called the loss function, cost function, or error function when minimizing the objective function or criterion. 

In deep learning, the objective function is usually the average of the loss functions.

A measure of how wrong your model's predictions are compared to the actual truth.

The loss is calculated by feeding the outputs of the model into the associated loss function

### Classification
Models usually output probabilities for each category as a result of the softmax layer (or activation)

* Hinge loss: ensures the correct category's score exceeds the sum of incorrect scores by a safety margin, making it the ideal "maximum-margin" penalty for Support Vector Machines.

* Cross-entropy loss: a measure how well your model's predicted probabilities align with the known labels in your training data. Similar to Maximum Likelihood Estimation (MLE) as it adjusts model weights.

### Regression
Single value as output

* Mean Squared Error (MSE): average measured of the squared difference between predictions and actual observations

* Mean Absolute Error (MAE): average measured of the sum of absolute differences between predictions and actual observations


## Gradient Descent
Iterative process used to find the specific set of weights and biases that make the network's output as close as possible to the actual target values.

Not common for gradient descent to be used directly in deep learning.

Why we prefer using quadratic cost function or MAE? Quadratic cost function provides a smooth gradient and reduces the risk of getting stuck in a local minimum.


### Stochastic Gradient Descent (SGD)
An optimized version of gradient descent designed to handle large datasets by drastically reducing the computational work required for each update.

SGD samples one index at random, calculates the gradient for only that one specific example, and updates the parameters.

### Mini-batch Stochastic Gradient Descent
Middle ground approach that balances the stability of Batch Gradient Descent with the speed of Stochastic Gradient Descent.

Instead of using the entire dataset (Batch) or just one single example (SGD), it uses a small, random subset of data points called a mini batch to calculate the gradient and update the model.


## Keras And TensorFlow
* User-friendliness

* Modularity: can combine neural layers, cost functions, optimizers, initialization schemes, activation functions and regularization schemes to create new models

* Easy extensibility: can create new modules

### Modeling Steps
1. Initialize the model container using Sequential()

2. Get input shape equal to the number of features in dataset (X_train.shape[1])

3. Specify the architecture (stacking layers) using the .add() method
    * First Hidden Layer: specify input shape, number of neurons, and activation function

    * Subsequent Hidden Layers: add more layers (no input shape)

    * Output Layer: the final layer is tailored to your goal (e.g., one neuron for regression)

4. Call model.summary()


### Compile
Bridges the model's architecture and the actual mathematical learning process.

1. Choosing the Optimizer (optimizer='adam'): updates the weights and biases based on the error

2. Choosing the Loss Function (loss='mean_squared_error'): tells the model how far its predictions are from the reality

### Fit
Where the actual training happens

* Epochs (epochs=10): An epoch is one full pass through the entire training dataset

* Batch Size (batch_size): Breaks up the data into smaller chunks

* Verbosity (verbose): shows the progress bar and loss for every epoch if set to 1

### Predict
Use the predict() method for estimation