### Object-detection-within-images

#### Stage 1:
Create dataset – we would like to create a dataset for the training of super-resolution network
Our basic dataset for this task will be the PascalVOC 2007 dataset which I shared with you here: https://drive.google.com/open?id=1UFoUNOznWKg9lOgYtuawgSasd5_rLWDF 
First created a dataset with images of 3 different sizes:
X - 72x72x3;      y_mid – 144x144x3;      y_large – 288x288x3
We loaded and generated the above arrays of input images, we would like to split them into training and validating our model, for simplicity, we will use the first 1000 images for validation and the rest for training. 
Next, we presented few images so that we can compare the training with our desired labels.
We get something like this as an output:

![image](https://user-images.githubusercontent.com/44158047/86541060-7adf6a00-bf12-11ea-97ae-2958c983de02.png)

#### Step 2:
Created an initial model
In this step we created the following (vanilla) model:




