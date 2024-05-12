# ME-UNet: an Memory Efficient Model for 3D Coronary Artery

## Introduction

This is the source code for the paper "ME-UNet: an Memory Efficient Model for 3D Coronary Artery". 

## Usage

1. Running Preprocess.py to generate the preprocessed data. 

   ```
   Python Preprocess.py --data_folder './data', --resolution 0 --interpolation 0 --target_folder ./clean_data
   ```

​	The illustration of parameters are as follows :

* --data_folder: the path of raw dataset
* --resolution: the scale of saved data. 0, 1, and 2 represent high resolution ($512\times 512\times 256$), middle resolution ($256\times 256\times 128$) and low resolution ($128\times 128\times 64$) respectively.
* --interpolation: the interpolation method used to resize the 3D images. 0, 1, 2, 3, 4 and 5 represent Nearest-neighbor interpolation, Bilinear interpolation, Quadratic interpolation, Cubic interpolation, Quartic (bi-quadratic) interpolation and Quintic interpolation respectively.
* --target_folder: the saved path.

2. Running main.py to train and test the model.

   ```
   Python main.py --data_folder './clean_data' --save_path './models/MEUNet_model.pth' --lr 0.01 --batch_size 1 --max_epoch 100 --patient 30 --feature_list [16, 32, 64, 128, 256]
   ```

   The illustration of parameters are as follows :

* --data_folder: the path of preprocessed dataset

* --save_path: model's saved path
* --lr: learning rate
* --batch_size: batch size for training , validating and testing
* --max_epoch: maximum epochs for training
* --patient: the parameter controls early stopping during training. If the validation loss fails to decrease after surpassing the specified number of epochs, denoted by `patient`, the training process will be halted.
* feature_list: the channel dimension at each level of U-Net backbone.

