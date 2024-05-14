#  Machine Learning for Action Detection

#### [Jorge Muñoz Zanón](https://jmuozan.github.io/mdef-website/)

As part of my thesis project on Future Learning focused on Arts and Crafts I decided to prototype for third MicroChallenge a machine learning model that can learn certain actions and tell you when you're doing them right or wrong. With a live camera prediction you'll be able to know if the movement is being done in the correct way.



## What files are available on the repo?

In this repository you'll find:

- `ML_Sequence_Recognition.ipynb` a Jupyter notebook with all the steps since the data collection and treatment to the training and real-time predictions
- `Real_Time_Pred.py` a python file with just the predictions in real time, in case you just want to test how it works
- `actions.h5` the model already trained
- `IMG` folder, with the images for this documentation
- `CSVs` for you to see how the data will look like during it's collection and treatment

## References

If you want to use ML to predict sequences but this structure doesn't fit to you I highly recommend to check the following tutorials where I've been inspired:

- [Nicholas Renotte: Sign Language Detection using ACTION RECOGNITION with Python | LSTM Deep Learning Model](https://www.youtube.com/watch?v=doDUihpj6ro&list=PLtjLv8XIYA2GPl5Pju2eebqfV9oOlB675&index=4)
- [Nicholas Renotte: AI Learns to Do Deadlifts](https://www.youtube.com/watch?v=H7cGq0xIHbc&list=PLtjLv8XIYA2GPl5Pju2eebqfV9oOlB675)
- [Nicholas Renotte: Training my deadlift bot with MediaPipe and OpenCV](https://www.youtube.com/watch?v=PGsAsuwBdw0&list=PLtjLv8XIYA2GPl5Pju2eebqfV9oOlB675&index=2)

## How does it work?

In this part I'm going to walk you through the different steps followed by my code. Also I will try to explain what errors you might get while trying to execute the code and how to solve them. (Also, if you find any error that is not solved here don't doubt on contacting me so I can update the documentation)

### 1st step: Get your data

Before starting, the first thing to do is to install and import the used dependencies. The first two blocks of the code will do that. We will mediapipe to detect all the points on our hands and body, Opencv to access the camera or video and pandas, numpy and matplotlib to prepare our data. Later we will install our dependencies for the training.

After installing and importing, if our goal is to be able to detect sequences the follow up part will be to know where to extract them from. For that you'll need a video. I highly recommend a high quality video where the light is good so the hands and body recognition will work best. If not the script is sited up for you to use your webcam, just as I did for the example of this repo.

The first big block of code (Cell 3) will make sure that your laptop can access your camera and draw the landmarks generated by mediapipe. The landmarks generated will be all the points detected in hands and body (Additionally you can also detect the points of your face, as I haven't made use of them here I haven't included them but if you're interested I recommend you to check on the mediapipe documentation). Once you test that the camera is working press `q` to exit the video.

***NOTE:** A common error will be that executing the cell gives you an error or opens up a camera you don't want to use, if this happens try to change the number on `cap = cv2.VideoCapture(0)` as depending on the cameras set up on your computer the number will be different. (On my MacBook number `0` corresponds to my webcam)

![](IMG/Video_1.gif)

Next up you'll record your video on Cell 4. If you have your video already recorded go straight to the next Cell. Cell 4 will be similar to cell 3 but this one won't show the landmarks of mediapipe. Here you will need to do the movements you want to capture. In other to use them for machine learning you will have to repeat them a bunch of times in the right and wrong way (In my test I captured two different movements and inside of each I captured around 30 times each way(right and wrong)). If you want to detect more than one movement right and wrong I will recommend to re-execute the cell and save different videos for different movements so that way can be more organized, even though it will work fine if it's just with one video.

Here's and schematic of how I recommend to do the video capturing so it will be easier to work with that later:

![](IMG/Schematic_1.png)





