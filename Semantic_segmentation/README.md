# Semantic segmentation for self-driving cars

Dataset used: CARLA dataset for semantic segmentation [1]

### Model 1

A simple U-Net with residual convolution blocks in both the encoding and decoding stages. This network lacks concatenation layers between the respective blocks of the encode and decode stages. The model architecture can be seen [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/Model_Architecture/mnist2FC.png). The implementation of this architecture is [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/notebooks/MNIST_2FC.ipynb). 

### Model 2 

A simple U-Net with residual convolution blocks in both the encoding and decoding stages. This network has concatenation layers between the respective blocks of the encode and decode stages. The model architecture can be seen [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/Model_Architecture/mnist2FC.png). The implementation of this architecture is [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/tree/main/Image_classification/MNIST/notebooks/MNIST_2FC.ipynb). 


# Methodology

The data is obtained from [1]. The dataset has 1000 images which is divided into 3 parts, namely, "train", "validation" and "test" (or evaluation data). Number of images per set is mentioned in Table 1. Train and validation datasets are used to train the model. All the input images are rescaled to [0-1] i.e. (divided by 255.) to normalise the input data. Each image is provided with a mask. The data is labelled for predicting 13 classes. 

The model is trained for 2 stages with incremental batch size. Batch sizes per stage can be seen in Table 2. 

##### Table 1. Number of images per set.

| Set | Number of images |
| ----- | --------- |
| Train | 800 | 
| Validation | 100 | 
| Test (Evaluation) | 100 |

##### Table 2. Train and validation batch sizes per stage.

| Stage | Train batch size | Validation batch size |
| ----- | --------- | --------- |
| stage1 | 16 | 8 |
| stage2 | 64 | 32 |


After the model is trained for 2 stages, the best weights are loaded and the model is evaluated on the test set (or the evaluation set). 

Both methods described above follows the same strategy.


# Results

Results predicted by the model 1.
| Input image | Image mask | Predicted mask |
| ----------- | ---------- | -------------- |
|![1](https://user-images.githubusercontent.com/43802985/95289742-22a96280-0889-11eb-8402-a9d5e30679c0.png)|![2](https://user-images.githubusercontent.com/43802985/95289829-60a68680-0889-11eb-9593-38ba2db25a06.png)|![3](https://user-images.githubusercontent.com/43802985/95289853-7025cf80-0889-11eb-8783-82e87f7d6f63.png)|

Results predicted by the model 2.
| Input image | Image mask | Predicted mask |
| ----------- | ---------- | -------------- |
|![1](https://user-images.githubusercontent.com/43802985/95289742-22a96280-0889-11eb-8402-a9d5e30679c0.png)|![2](https://user-images.githubusercontent.com/43802985/95289829-60a68680-0889-11eb-9593-38ba2db25a06.png)|![3](https://user-images.githubusercontent.com/43802985/95289853-7025cf80-0889-11eb-8783-82e87f7d6f63.png)|

The predicted mask is based on the colour map provided in [1].

# References

[1] https://carla.readthedocs.io/en/latest/ref_sensors/#semantic-segmentation-camera
