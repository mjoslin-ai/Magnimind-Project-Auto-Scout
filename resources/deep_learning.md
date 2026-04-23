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


## Loss Functions


