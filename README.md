# Camera Model Identification 

## Introduction  
I created this project to become familiar with the ResNet structure; in particular, I ultimately create a ResNet50 model (as seeen in the ResNet50 notebook) 
I then use the network to train on the dataset for a [Kaggle Competition](https://www.kaggle.com/c/sp-society-camera-model-identification) to try and learn 
which camera model was used to take a particular photograph. 

## The Data
The data comes from two sources, which are explained in the `More Data` notebook (from Kaggle and scraped from Flickr). In my implementation, I perform the same types 
of manipulation as described in the competition (resize, compression, gamma adjustment) and then crop the images to be 512x512x3. As I don't have a whole lot of system 
memory, I introduce a `load` function that will load a random subset of the data based on a ratio parameter to be used; this is repeated for each training epoch. 

## The Network
The ResNet50 structure is followed pretty closely, with only the final fully-connected layer being different. Since the network only accepts 224x224x3 images, I sample 
each of the training images via a center crop and then a few more times from random positions. The network was then trained for roughly 30 epochs of ~20k images. 

## The Results
Ultimately, I only achieved about a **50%** test accuracy. I did not have more time to explore why, but I suspect a few reasons: 
- Errors in my data generation
- Not enough training time
- No data pre-processing 
Really, I likely would've gotten further had I taken the time to build out a confusion matrix for both altered and unaltered images to see where the biggest issues were. 

## Other Notebooks
Other than the `More Data` and `ResNet50` notebooks, there are 5 notebooks; they are marginally functional at best, but I included them as they track my progress leading 
up to the final two notebooks. 
