# Eye For Blind
## Introduction
The World Health Organization (WHO) has reported that approximately 285 million people are visually impaired worldwide, and out of these 285 million, 39 million are completely blind. It gets extremely tough for them to carry out daily activities, one of which is reading. From reading a newspaper or a magazine to reading an important text message from your bank, it is tough for them to read the text written in it.

 
A similar problem they also face is seeing and enjoying the beauty of pictures and images. Today, in the world of social media, millions of images are uploaded daily. Some of them are about your friends and family, while some of them are about nature and its beauty. Understanding what is present in that image is quite a challenge for certain people who are suffering from visual impairment or who are blind.


In an initiative to help them experience the beauty of the images, Facebook had earlier launched a unique feature earlier that can help blind people operate the app on their mobile phones. The feature could explain the contents of an image that their friends have posted on Facebook. So, say, if someone posted a picture with their dog in the park, the application would speak out the contents and may describe it like, “This image may contain a dog standing with a man around the trees.”


In this project, I will attempt to make a ML model that is similar to the one developed by Facebook, specifically such that a blind person knows the contents of an image in front of them with the help of a CNN-RNN based model. The model will convert the contents of an image and will provide the output in the form of audio.

## Problem Statement
To create a deep learning model based solution which can explain the content of an image in the form of an audio through caption generation using attentaion mechanism on Flickr8 Dataset.

## Approach
We are going to base our approach on an approach similar to the one proposed in [[1]](#1).

This solution will take an image as its input and play an audio describing the contents of image as its output.

At a highlevel, the solution has two distinct parts

1. __Image to Text Generator (ITG):__ This is reposnsible for taking an image as input and generating a textual description of the content of image in English language. The text thus generated would serve as input to the second part of the solution. ITG would be a CNN-plus-RNN based model which would generate caption for the input image.
2. __Text To Speech Converter (TTSC):__ This part is responsible for taking an English language text as input and play an audio equivalent of the input text. This part of the solution would make use of a Text-To-Speech library to convert caption to a speech.


## Outline of Solution
We are attempting to solve two Machine Vision problems

1. Object Detection in a given image
2. Capturing relationships between detected objects

An image can be easily fed to a CNN to extract high level features. These highlevel features can then act as an input to an RNN, which can generate caption from the input text description of detected objects and their relationships.

Solution to the first part of problem is releatively easier. The challenging part is not just to capture relation ships beteen detected objects, but also to find out the object which is going to be the "focus area" for the caption. In this sense, we  need some way to give "attention" to sepcific parts of the image. Therefore, we would be using approach called 'Attention Model' and extend our CNN-RNN model to include an Attention model. This Attention model would sit in between CNN and RNN. The job of Attention model would be proveide input to RNN, but only for the portion which is having "attention". See [[1]](#1) for an excellent work on Attention Models, which serves as basis for our solution.

## References
<a id="1">[1]</a> 
[Show, Attend and Tell: Neural Image Caption Generation with Visual Attention]( 
https://arxiv.org/abs/1502.03044) by Kelvin Xu, Jimmy Ba, Ryan Kiros, Kyunghyun Cho, Aaron Courville, Ruslan Salakhutdinov, Richard Zemel, Yoshua Bengio.