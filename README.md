# Cats-and-Dogs---Binary-Image-Classification

1. Binary Image Classification:

CNN ( Convulational Neural Network ). One of the most popular uses of CNN is image classification.Facebook uses CNN for automatic image tagging, Amazon for product recommendation, Google for search through user's photos

I used Python syntax.

I used framework Keras. Keras is a high level neural network API written in Python. But Keras does not work by itself. It needs a backend - Googles' Tensorflow

I used matplotlib for plotting graphs.

Downloaded original dataset from Kaggle. Now we will divide training data set into train and validation ( 3000 : 1000). For this we create a folder 'Small'.

Now there are 4 steps :
Model Construction
Model Training
Model Testing
Model Evaluation

Model Construction:
- Used CNN
- we use sequential layer, hence model = Sequential()
- model.add will describe each layer. Each layer consists of Conv2D + Relu ( activation function ) followed by Maxpooling 2D layer. It is then followed by 2 dense layers. The number 32 in Conv2D represents the amount of output filter in convolution.Number 3,3 show the width and height of 2D convolution window.Important aspect of first Conv2D layer is the input. following layers are same but without input.
Maxpooling is used to downsize sample. Here, (2,2) denote the pool size that halves the input in both spatial dimensions.
After this there are 2 dense layers, the input to which is from flatten layer.
First Dense layer, has output 512 with Relu Activation function
Second Dense layer, has output 1 with Sigmoid activation function
- After sufficient number of layers have been added, Keras will communicate with TensorFlow to compile t
le model
- Before compilation, it is also important to add loss function and optimizer
Binary cross entropy loss function will show sum of all individual losses
RMSprop optimiser is good for recurrent neural network
- Now we have to scale for further use.
====================
Model Training:
- model.fit_generator
- save the model using command: model.save
- Epoch = how many times training will repeat
- From the plot, we can see that the Training accuracy reaches 85% while validation accuracy is 82%. hence we see there is loss in accuracy , which is due to overfitting. Also the Training loss is 34% while Validation loss is 43%. Now we try to increase the accuracy through data augmentation approach.
- ImageDataGenerator quickly sets up Python generators that can convert image files on disk to batches of preprocessed tensors.Generate batches of tensor image data with real-time data augmentation. The data will be looped over (in batches).


- To further fight overfitting, we will also add a Dropout layer to our model, right before the densely-connected classifier
- From the plot, we see that Training accuracy reaches 84% while validation accuracy is 88%

Model testing:
test accuracy = 89%

========================
Feature extraction by Extending the model (`conv_base`) by adding `Dense` layers on top, 
and running the whole thing end-to-end on the input data

Test accuracy = 89.7%
