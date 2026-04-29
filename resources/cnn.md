# Magnimind

CNN


## Kernel
Matrix of weights used to extract features from an input image

* Also called a filter

* If kernel has a shape of 3x3, it means the filter is a square grid consisting of 9 total pixels (weights).


## Convolution
Reduces the number of parameters to estimate using shared weights (and the bias) across an image

In a dataset with face images:

* Initial process: reveal features such as edges, corners, and round regions in the image

* subsequent process: reveal that there are features such as eyes and noses in the picture

* subsequent process: reveal that this is a face

* Last process: determined who belongs to this face


## Padding
Adds extra pixels (usually zeros) around the kernel border

Prevents data loss at the edges and maintains image dimensions


## Stride
Defines how many pixels the kernel shifts at a time as it slides across the image


## Improving CNNs performance

To prevent overfitting:

* Pooling: (usually Max Pooling) reduces the spatial dimensions (width and height) of the input.

    * removes dependence on dimensionality of original image

* Dropout: randomly shuts off a subset of neurons in a layer for each iteration in the training phase

To improve performance:

* Batch Normalization: used to make neural networks faster (finding local minimum) and more stable by re-scaling the data between layers

* Data Augmentation: method for creating more data by making small changes 

    * cropping
    * padding
    * horizontal flipping

    In Keras, we can do this with ImageDataGenerator in preprocessing.image module



cross-correlation