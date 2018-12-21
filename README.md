# Udacity-Behavioral-Cloning

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)
  
This project uses convolutional neural network to predict steering angle from image and drive a car in the simulator.
  

![track1](https://user-images.githubusercontent.com/13807244/33979745-bb3e7400-e0e0-11e7-8a42-fd4cb20ed0ec.gif)  
[link to youtube video](https://www.youtube.com/watch?v=bQS9oFGehEU)

# Overview
In this project, I will use what you've learned about deep neural networks and convolutional neural networks to clone driving behavior. I will train, validate and test a model using Keras. The model will output a steering angle to an autonomous vehicle.

### Project Files
|  Filename   |   Description  | 
|:-------------:|:-------------:|
| prepare_data.ipynb |  ipython notebook for data preprocessing and argumentation |
| model.py | define and train the neual network |
| model.h5 | saved model by keras |
| drive.py | communicate with simulator and use saved model to predict steering angle  |

### Usage
Download simulator from [thie repository](https://github.com/udacity/self-driving-car-sim), run the simulator in 
autonomous mode and execute following command:
```
> cd SDC_Engineer/CarND-Behavioral-Cloning-P3/
> source /Users/gongjianxin/anaconda3/bin/activate carnd-term1
> python drive.py model.h5
```

### Data Preprocessing & Argumentation
Here I use the [Udacity sample data](https://d17h27t6h515a5.cloudfront.net/topher/2016/December/584f6edd_data/data.zip). 
The distribution of data is skewed due to the track and the way simulator records data:  
![original_distribution.png](https://user-images.githubusercontent.com/13807244/33977428-cb020d94-e0d5-11e7-9d2a-cd01ca414daa.png)
  
After dropping 80% of data with 0 steering angle, left & right camera images are used with angle correction and data argumentation is
applied to the center image. Images are cropped and resized to 75x320x3 shape. For each row of data in csv file, 8 images are generated (or 7 since image with 0 steering angle won't
be flipped):  
![generated_data](https://user-images.githubusercontent.com/13807244/33977685-fa3108d0-e0d6-11e7-9822-bbaec7a4e4cd.png)
  

Here I tried different distribution by subsampling the generated data and decided to use all generated data. 
The final distribution looks like:  
![final_distribution](https://user-images.githubusercontent.com/13807244/33977734-498b742e-e0d7-11e7-97b2-bb32d0e91e02.png)

### Model Architecture and Training
The model is based on [Nvidia's paper](http://images.nvidia.com/content/tegra/automotive/images/2016/solutions/pdf/end-to-end-dl-using-px.pdf) 
with following modification:
* use input shape of 75x320x3 instead of 66x200x3
* use rgb channel instead of yuv
* remove first fully connected layer with 1164 neurons
* add a dropout layer to avoid overfitting
* use elu instead of relu as activate function of covolution layer

The training uses mean squared error as cost function and Adam optimizer with 0.001 learning rate,
10% data as validation data, 5 epochs and batch size of 32.

  
![model](https://user-images.githubusercontent.com/13807244/33979506-991f9d3c-e0df-11e7-8ba8-830c0dfda74e.png)
  
