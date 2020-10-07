# Semantic segmentation for self-driving cars

Dataset used: CARLA dataset for semantic segmentation [1]

### Model 1

A simple U-Net with residual convolution blocks in both the encoding and decoding stages. This network lacks concatenation layers between the respective blocks of the encode and decode stages. The model architecture can be seen [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/blob/main/Semantic_segmentation/Model_Architectures/simple_RES_Unet_260820.png). The implementation of this architecture is [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/blob/main/Semantic_segmentation/notebooks/Seg_simple.ipynb). 

### Model 2 

A U-Net with residual convolution blocks in both the encoding and decoding stages. This network has concatenation layers between the respective blocks of the encode and decode stages. The model architecture can be seen [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/blob/main/Semantic_segmentation/Model_Architectures/conc_RES_Unet_310820.png). The implementation of this architecture is [here](https://github.com/SivanandaGorugantu/convolutional_neural_networks/blob/main/Semantic_segmentation/notebooks/Seg_concat.ipynb). 


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
|![molde1_input](https://user-images.githubusercontent.com/43802985/95327073-2658db80-08c1-11eb-88db-da65ac4b6519.png)|![model1_mask](https://user-images.githubusercontent.com/43802985/95327060-22c55480-08c1-11eb-8d0b-55fadc5ec588.png)|![model1_pred](https://user-images.githubusercontent.com/43802985/95327063-23f68180-08c1-11eb-8b0b-39b63a5b608a.png)|

Results predicted by the model 2.
| Input image | Image mask | Predicted mask |
| ----------- | ---------- | -------------- |
|![model2_input](https://user-images.githubusercontent.com/43802985/95327064-248f1800-08c1-11eb-97c6-d0b3ea601db5.png)|![model2_mask](https://user-images.githubusercontent.com/43802985/95327068-2527ae80-08c1-11eb-994b-47670c47fd06.png)|![model2_pred](https://user-images.githubusercontent.com/43802985/95327072-25c04500-08c1-11eb-92db-de4ffe940faf.png)|

The predicted mask is based on the colour map provided in [1].

# References

[1] https://carla.readthedocs.io/en/latest/ref_sensors/#semantic-segmentation-camera
