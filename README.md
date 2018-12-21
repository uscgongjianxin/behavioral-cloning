# Udacity-Behavioral-Cloning

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)
  
This project uses convolutional neural network to predict steering angle from image and drive a car in the simulator.
  

![track1](https://user-images.githubusercontent.com/13807244/33979745-bb3e7400-e0e0-11e7-8a42-fd4cb20ed0ec.gif)  

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
  
