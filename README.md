Team 16:
========
Aditya Nagesh Govardhan
Lekhavarshini Selvam
Ronik Dhakar

## Installing

These instructions are for a fresh Ubuntu 18.04 box. Most of the same should apply to OS X. If you have issues installing, feel free to contact at agovardh@asu.edu

### Basics

Recent Ubuntu releases come with python3 installed. I use pip3 for installing dependencies so install that with `sudo apt install python3-pip`. 

### Python dependencies

`pip3 install numpy keras h5py`

That should install a slew of other libraries you need as well.

### Install Pygame

Install Pygame's dependencies with:

`sudo apt install mercurial libfreetype6-dev libsdl-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsmpeg-dev libportmidi-dev libavformat-dev libsdl-mixer1.2-dev libswscale-dev libjpeg-dev`

Then install Pygame itself:

`pip3 install hg+http://bitbucket.org/pygame/pygame`

### Install Pymunk

This is the physics engine used by the simulation. It just went through a pretty significant rewrite (v5) so you need to grab the older v4 version. v4 is written for Python 2 so there are a couple extra steps.

Go back to your home or downloads and get Pymunk 4:

`wget https://github.com/viblo/pymunk/archive/pymunk-4.0.0.tar.gz`

Unpack it:

`tar zxvf pymunk-4.0.0.tar.gz`

Update from Python 2 to 3:

`cd pymunk-pymukn-4.0.0/pymunk`

`2to3 -w *.py`

Install it:

`cd ..`
`python3 setup.py install`

Now go back to where you cloned `reinforcement-learning-car` and make sure everything worked with a quick `python3 learning.py`. If you see a screen come up with a little dot flying around the screen, you're ready to go!

## Training

First, you need to train a model. This will save weights to the `saved-models` folder. *You may need to create this folder before running*. You can train the model by running:

`python3 learning.py`

It can take anywhere from an hour to 36 hours to train a model, depending on the complexity of the network and the size of your sample. However, it will spit out weights every 25,000 frames, so you can move on to the next step in much less time.

## Playing

Edit the `playing.py` file to change the path name for the model you want to load.

Then, watch the car drive itself around the obstacles!

`python3 playing.py`

That's all there is to it.

## Plotting

Once you have a bunch of CSV files created via the learning, you can convert those into graphs by running:

`python3 plotting.py`

This will also give out a bunch of loss and distance averages at the different parameters.


