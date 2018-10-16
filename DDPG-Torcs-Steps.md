# DDPG-Keras-Torcs-Simulator-Setup

This simulator setup is with respect to the Github repository https://github.com/yanpanlau/DDPG-Keras-Torcs for **Reinforcement learning** using **Torcs simulator**.

Below is the brief installation procedure 
```
git clone https://github.com/yanpanlau/DDPG-Keras-Torcs.git
cd DDPG-Keras-Torcs
cp *.* ~/gym_torcs
cd ~/gym_torcs
python ddpg.py
```

This may not work directly as there are dependencies which needs to be installed.

Lets see the detailed steps and errors encountered during the setup.

If you have not installed dependancy packages and directly going for the 5 steps mentioned above, you might get the below errors

###Error 1 <br />
**Details : No module names Gym.**
```
kk@kk-Lenovo-ideapad-320-15ISK:~/gym_torcs$ python ddpg.py 
Traceback (most recent call last):
  File "ddpg.py", line 1, in <module>
    from gym_torcs import TorcsEnv
  File "/home/kk/gym_torcs/gym_torcs.py", line 1, in <module>
    import gym
ImportError: No module named gym
```
**Fix :** **Install gym** using the below procedure
```
kk@kk-Lenovo-i

deapad-320-15ISK:~/gym_torcs$ pip install gym[all]
```

###Error 2 <br />
**Details : Failed Failed building wheel f0or Box2D-kengz while installing gym**
```
Command "/usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-nlkdIE/Box2D-kengz/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --record /tmp/pip-6P0gPk-record/install-record.txt --single-version-externally-managed --compile --user --prefix=" failed with error code 1 in /tmp/pip-build-nlkdIE/Box2D-kengz/
```
**Fix : Install below packages before installing gym**
```
xvfb 
libav-tools 
xorg-dev 
libsdl2-dev 
swig 
cmake
```
After re-installing these packages, re-start the installation of gym[all]

###Error 3 <br />
**Details : No module named keras.models**
```
kk@kk-Lenovo-ideapad-320-15ISK:~/gym_torcs$ python ddpg.py 
Traceback (most recent call last):
  File "ddpg.py", line 5, in <module>
    from keras.models import model_from_json, Model
ImportError: No module named keras.models
```
**Fix : Install keras**
```
kk@kk-Lenovo-ideapad-320-15ISK:~/gym_torcs$  sudo pip install keras==1.1.0
```

###Error 4 <br />
**Details : ImportError: No module named tensorflow**
```
kk@kk-Lenovo-ideapad-320-15ISK:~/gym_torcs$ python ddpg.py 
Using TensorFlow backend.
Traceback (most recent call last):
  File "ddpg.py", line 5, in <module>
    from keras.models import model_from_json, Model
  File "/usr/local/lib/python2.7/dist-packages/keras/__init__.py", line 2, in <module>
    from . import backend
  File "/usr/local/lib/python2.7/dist-packages/keras/backend/__init__.py", line 64, in <module>
    from .tensorflow_backend import *
  File "/usr/local/lib/python2.7/dist-packages/keras/backend/tensorflow_backend.py", line 1, in <module>
    import tensorflow as tf
ImportError: No module named tensorflow
```
**Fix : Install tensorflow** 
```
sudo pip install tensorflow==0.12.0
```

###Error 5 <br />
**Details : After clearning above error when you run ```python ddpg.py``` you might see the torcs simulator relaunches itself repeatedely.**
**Fix : Install vtorcs-RL-color by following below steps**

a. Install the below dependancy packages.
```sudo apt-get install libglib2.0-dev  libgl1-mesa-dev libglu1-mesa-dev  freeglut3-dev  libplib-dev  libopenal-dev libalut-dev libxi-dev libxmu-dev libxrender-dev  libxrandr-dev libpng12-dev ``` <br />
b. cd into the ```vtorcs-RL-color``` directory which is inside gym directory. <br />
c. ```./configure``` <br />
d. ```make``` <br />
e. ```make install``` <br /> 
f. ```make datainstall``` <br />

Note : If you face errors in make steps, that would be due to the permission issue. So might have to re-run make with sudo

Now if you could run ```python ddpg.py``` you should be able to see the simulator running. 

###Error 6 <br />
**Details : Relaunching issue may not get fixed after implementing the above solution. And also you may see some errors related to xte from autostart.sh file **
**Fix : Install xautomation by running below command **
```
sudo apt-get install xautomation
```

This document would be updated as and when I find new errors or issues. 

Thank you. 
