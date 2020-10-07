# MNIST

The aim of this project was two-fold. Firstly, to solve the classification problem of MNIST handwritten digits. Secondly, to compare and evaluate different architectures based on certain factors.

MNIST dataset[1] available in Keras consists of 60,000 training grayscale images and 10,000 test grayscale images of dimensions 28x28. The test image set was used to evaluate model performance. The train set was further divided into train and validation sets for model training based on 80-20 rule. Three different architectures were used in this experiment. Each model was evaluated based on the number of model parameters and evaluation loss and accuracy.

### Method 1 - Plain CNN

This is a custom plain CNN with a total of 96,774 parameters (96,292 trainable and 482 non-trainable). The model architecture as seen [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/Model_Architecture/mnist2FC.png), has 4 blocks of sequential convolutional layers and 2 fully connected layers. The implementation of this architecture is [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/notebooks/MNIST_2FC.ipynb). The output of each layer is also visualised in this notebook for better understanding of the model performance.

### Method 2 - CNN with Concat layers

A custom architecture with a total of 270,482 parameters (269,792 trainable and 690 non-trainable). It has 4 blocks of convolutional layers with each block's output concatenated with its input and fed as input to its subsequent conv2d layer. This architecture also has 2 fully connected layers. The architecture is visualized [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/Model_Architecture/mnist2FC_concat.png).

### Method 3 - Residual Network

A residual network model with a total of 134,472 parameters (133,668 trainable and 804 non-trainable). This model has 2 residual blocks and no fully connected layers. The model architecture can be seen [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/Model_Architecture/mnist_Res.png).

# Comparison

The train vs validation accuracies of each of the methods described above after the 1st stage of training can be seen below in figures 1-3.

##### Figure 1. Method 1

![](https://raw.githubusercontent.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/.github/images/method1.png)

##### Figure 2. Method 2
![](https://raw.githubusercontent.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/.github/images/method2.png)

##### Figure 3. Method 3
![](https://raw.githubusercontent.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/.github/images/method3.png)

##### Table 1. Evaluation accuracy and loss of each method.

| Method | Accuracy | Loss |
| ------ | -------- | ---- |
| method1| 98.93% | 0.04278 |
| method2| 99.2% | 0.03197 |
| method3| 99.51% | 0.01494 |

As seen in Table 1, method 3  performed reasonably well with an evaluation accuracy of 99.51%. We can also observe that with approximately 38,000 more parameters, method 3 achieved significant improvement over method 1. Also, method 3 has half the number of parameters as compared to method 2.

# Results

Some results predicted by the models can be seen below.

![](https://raw.githubusercontent.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/.github/images/1.png)
![](https://raw.githubusercontent.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/.github/images/2.png)
![](https://raw.githubusercontent.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/.github/images/3.png)


# Conclusion

The experiment was to understand which method performs best based on factors such as the total number of model parameters, evaluation accuracy and loss. Method 3 (residual network) performed better than the other 2 methods with achieving an evaluation accuracy of 99.51%. However, there is a huge scope for improvement with further experimentation and finetuning. One can seek to achieve better performance:
1. with a different and better model architecture.
2. adding more image augmentation parameters during the model training phase.
3. Finetuning the model hyperparameters.

# References

[1] http://yann.lecun.com/exdb/mnist/
