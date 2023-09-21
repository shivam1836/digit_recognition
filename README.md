# digit_recognition
This repository is for practice of implementing well-known network architectures and ensembling methods, including the followings:

Architectures
Mobilenet - [structure] [training progress]
VGG16 - [structure] [training progress]
Resnet164 - [structure] [training progress]
WideResnet28-10 - [structure] [training progress]
Ensembling methods
Unweighted average
Majority voting
Super Learner - [structure]
Others
Channel-wise normalization of input images: substracted by mean and divided by std
Data augmentation: rotation, width shift, height shift, shearing, zooming
Environment
MacOS High Sierra 10.13.1 for implementation / Ubuntu 14.04 for training
Python 3.6.3
Keras 2.1.2 (Tensorflow backend)
Evaluation
The best single model and the best ensemble method achieve 99.76% and 99.77% on the test set respectively.

Model	On the validation set	On the test set
Mobilenet	99.63%	99.68%
 VGG16	99.61%	99.68%
Resnet164	99.72%	99.70%
WideResnet28-10	99.72%	99.76%
Ensemble (all)	On the validation set	On the test set
Unweighted average	99.70%	99.75%
Majority voting	        99.71%          	      99.76%      
Super Learner	99.73%	99.77%
In order to run the evaluation, it requires pre-trained weights for each model, which can be downloaded here.

*All pre-trained weights should be stored in './models'.

How to run
python evaluate.py [options]
Options
$ python evaluate.py --help
usage: evaluate.py [-h] [--dataset DATASET]

optional arguments:
  -h, --help         show this help message and exit
  --dataset DATASET  training set: 0, validation set: 1, test set: 2
Training
The training can be executed by the following command. Every model has the same options.

How to run
$ python vgg16.py [options]
Options
$ python vgg16.py --help
usage: vgg16.py [-h] [--epochs EPOCHS] [--batch_size BATCH_SIZE]
                [--path_for_weights PATH_FOR_WEIGHTS]
                [--path_for_image PATH_FOR_IMAGE]
                [--path_for_plot PATH_FOR_PLOT]
                [--data_augmentation DATA_AUGMENTATION]
                [--save_model_and_weights SAVE_MODEL_AND_WEIGHTS]
                [--load_weights LOAD_WEIGHTS]
                [--plot_training_progress PLOT_TRAINING_PROGRESS]
                [--save_model_to_image SAVE_MODEL_TO_IMAGE]

optional arguments:
  -h, --help            show this help message and exit
  --epochs EPOCHS       How many epochs you need to run (default: 10)
  --batch_size BATCH_SIZE
                        The number of images in a batch (default: 64)
  --path_for_weights PATH_FOR_WEIGHTS
                        The path from where the weights will be saved or
                        loaded (default: ./models/VGG16.h5)
  --path_for_image PATH_FOR_IMAGE
                        The path from where the model image will be saved
                        (default: ./images/VGG16.png)
  --path_for_plot PATH_FOR_PLOT
                        The path from where the training progress will be
                        plotted (default: ./images/VGG16_plot.png)
  --data_augmentation DATA_AUGMENTATION
                        0: No, 1: Yes (default: 1)
  --save_model_and_weights SAVE_MODEL_AND_WEIGHTS
                        0: No, 1: Yes (default: 1)
  --load_weights LOAD_WEIGHTS
                        0: No, 1: Yes (default: 0)
  --plot_training_progress PLOT_TRAINING_PROGRESS
                        0: No, 1: Yes (default: 1)
  --save_model_to_image SAVE_MODEL_TO_IMAGE
                        0: No, 1: Yes (default: 1)
File descriptions
├── images/ # model architectures and training progresses
├── predictions/ # prediction results to be used for fast inference
├── models/ # model weights (not included in this repo)
├── README.md
├── base_model.py # base model interface
├── evaluate.py # for evaluation
├── utils.py # helper functions
├── mobilenet.py
├── vgg16.py
├── resnet164.py
├── wide_resnet_28_10.py
└── super_learner.py
References
Papers
Very Deep Convolutional Networks for Large-Scale Image Recognition
Deep Residual Learning for Image Recognition
Identity Mappings in Deep Residual Networks
Wide Residual Networks
The Relative Performance of Ensemble Methods with Deep Convolutional Neural Networks for Image Classification
Implementation
ResNet Author's Implementation
WideResNet Author's implementation
MobileNet in Keras
How far can we go with MNIST??
Others
Global weight decay in keras? - Stackoverflow
Best up to date result on MNIST dataset - Kaggle
Batch Normalization before or after ReLU? - Reddit
Depth-wise Conv2D - Tensorflow Document
A Complete Tutorial on Ridge and Lasso Regression in Python
