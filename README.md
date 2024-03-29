# Dog-Identification-App-using-CNN
App taking image as an input and using CNN network to identify dog breed

## Description
This notebook accepts any user-supplied image as input. If a dog is detected in the image, it will provide an estimate of the dog's breed. If a human is detected, it will provide an estimate of the dog breed that is most resembling.

This project is part of Udacity's Nanodegree "Deep Learning".

## Dependencies
The notebook uses VGG16 pre-trained model which is downloaded from PyTorch library.
It also uses a haarcascade classifier for human face detection. The classifier is provided in the haarcascades folder.

The training requires two datasets, one for dogs and one from human faces.
Datasets can be downloaded in the notebook from these paths:
- dogs: https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip
- humans: https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/lfw.zip

## Installation
- Download the repository
- Download the datasets and follow instructions from the notebook to create the appropriate folders.

## Run the notebook
- Insert your own images that you would like to classify in the folder "my_images". The notebook will scan through all saved images and return a prediction.
- Run the Jupyter notebook providing your own pictures to the model.

## Notebook structure
- Import Datasets
- Create human face detector. This part uses a haarcascade classifier.
- Create dog breed detector. This part uses VGG-16 pretrained model.
- Create CNN architecture to classify dog breed from scratch
- Create CNN model to classifiy dog breeds using transfer learning
- Assemble algorithm of the detection App
- Test algorithm

## Results
The CNN architecture is build around five CONV2D layers with maxpooling and ReLu activation function. The last three layers use fully connected layers with softmax classifying dogs over 133 different breeds.
The model was trained on GPU and achieved a poor performance.

The second architecture uses transfer learning: from the VGG-16 pretrained network, I replaced the last layer with a simple fully connected classifier using softmax.
`model_transfer.classifier[6] = nn.Linear(4096, num_classes)`

Only the fully connected section of the model was re-trained. The performance achieved was 70% with only 10 epochs on GPU.

Detection samples:

![](/images/dog.PNG)

![](/images/human.PNG)

![](/images/dog2.PNG)

![](/images/nodog.PNG)
