# Udacity-Behavioral-Cloning

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)
  
This project uses convolutional neural network to predict steering angle from image and drive a car in the simulator.
  

![track1](https://user-images.githubusercontent.com/13807244/33979745-bb3e7400-e0e0-11e7-8a42-fd4cb20ed0ec.gif)

Example video by [Tianhong Chu](https://github.com/CtheSky/Udacity-Behavioral-Cloning)

# Overview
In this project, I will use what you've learned about deep neural networks and convolutional neural networks to clone driving behavior. I will train, validate and test a model using Keras. The model will output a steering angle to an autonomous vehicle.

### Project Files
|  Filename   |   Description  | 
|:-------------:|:-------------:|
| behavior_cloning_test.ipynb |  ipython notebook for data preprocessing and argumentation |
| model.py | create and train the model |
| model.h5 | a trained Keras model |
| drive.py | script to drive the car - feel free to modify this file |

### Usage
Download simulator from [thie repository](https://github.com/udacity/self-driving-car-sim), run the simulator in 
autonomous mode and execute following command:
```
> cd SDC_Engineer/CarND-Behavioral-Cloning-P3/
> source /Users/gongjianxin/anaconda3/bin/activate carnd-term1
> python drive.py model.h5
```
#### Saving a video of the autonomous agent

```sh
python drive.py model.h5 run1
```

The fourth argument, `run1`, is the directory in which to save the images seen by the agent. If the directory already exists, it'll be overwritten.

### `video.py`

```sh
python video.py run1
```

Creates a video based on images found in the `run1` directory. The name of the video will be the name of the directory followed by `'.mp4'`, so, in this case the video will be `run1.mp4`.

Optionally, one can specify the FPS (frames per second) of the video:

```sh
python video.py run1 --fps 48
```

Will run the video at 48 FPS. The default FPS is 60.

### Tips
- Please keep in mind that training images are loaded in BGR colorspace using cv2 while drive.py load images in RGB to predict the steering angles.

License
---
[MIT License](https://choosealicense.com/licenses/mit/#)

Copyright (c) [2018] [Jianxin Gong]
