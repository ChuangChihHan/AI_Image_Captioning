# AI_Image_Captioning
## Introduction
##### As technology advances, smartphones and social medias become an indepensable part in human beings’ lives. Nevertheless, for social medias such as Facebook and Instagram using images to deliver messages are difficult for blinds to perceive, let along for them to be involved in using these social medias. Therefore, we hope to apply techniques including image processing and natural language processing to describe the context in the images and then transform them in braillie or voice messages. Eventually, we hope to assist blinds to participate more in using social medias and thus be more involved in society.

## Dataset
Flickr8k dataset consisted of 8091 images and 40445 captions. Each image in the dataset will correspond to 5 picture captions.
The datasets is from Pytorch and is available on https://www.kaggle.com/datasets/adityajn105/flickr8k
##### Data Preprecessing
Image: We resize the image to 256*256, then use CenterCrop to crop the edges of the image. The final size of the images will be 224*224. \
Caption: We uniformly convert letters to lowercase, and add <start>, <end> before and after the captions!

## Method
##### We use Resnet50 model to preprocess our images into 1*2048-dim tensors. Then we average the tensors and input them into our model. Due to the fact that we generate a word for each time step, LSTM cell would be our choice of framework. In each time step, we use attention model to adjust the weights of previous generated words to strengthen the importance of our keyword in the captions. For lost function, cross entropy loss is computed in each caption, therefore one image will have 5 losses. Our best model has a combination of 4 layers, number of nodes [16, 32, 32, 16], and no activations, achieving 0.99% error on test set. Using first 100 cycles to predict capacities from 500 to 700, 600 to 800, and 700 to 900 have a test error 1.07%, 2.24%, and 1.79% respectively.

Click [Code link](https://colab.research.google.com/drive/1sGQaDv5RaqCnhIKHLCzodKROOjBC4UNJ) to see the model details.
