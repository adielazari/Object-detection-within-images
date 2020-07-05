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

![image](https://user-images.githubusercontent.com/44158047/86541081-abbf9f00-bf12-11ea-80a3-a160b614f1b7.png)

We fitted this model to our data using X_train and y_mid_train only

#### Step 3:
We added another block to our model so now we have both 144x144x3 output along with 288x288x3 output as follows:

![image](https://user-images.githubusercontent.com/44158047/86541105-ddd10100-bf12-11ea-827d-b18ac9e5f7ab.png)

#### Step 4:
Added residual blocks into the process
The residual blocks that we added were defined as a function with no arguments that returns a model.
We later used this residual block definition within our model prior to every UpSampling layer
We spended a moment to think, what should be the input and output of the residual-block model.

![image](https://user-images.githubusercontent.com/44158047/86541161-5afc7600-bf13-11ea-8b43-babf39b457bb.png)

#### Step 5:
Replaced the residual blocks we defined above with a dilated convolutional block as described below:






