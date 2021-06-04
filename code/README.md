# Project 7: Turtlebots Following Each Other

This is group 4's project for 41014 Sensors and Control for Mechatronic Systems.
Following the steps below should allow you to run the project for yourself where, 
a turtlebot follows another turtlebot in the same environment.

Group 4 Members: Prathyush Chatry, Kyle Pereira, Katie Powell


## Getting Started

This section will help you prepare for running the code on your local machine.
This project was completed on Ubuntu 16.04 and ROS Kinetic.


### Prerequisites

This is a list of things you will need to install if you haven't already:

* Files from the shared project Google Drive folder (link already provided in email)
* Turtlebot3 set-up files and simulation files from Robotis

If any problems occur an option will be to update anything you had previously
installed as the project was created using the most updated file versions as of 6/6/2020.


### Installation

1 If you have already installed appropriate files from Robotis and have experience with using 
the Turtlebot3 you may skip down to part 2.

If you haven't please go to (https://emanual.robotis.com/docs/en/platform/turtlebot3/setup/#setup)
to set up your pc with Ubuntu, ROS and a catkin workspace and install the Dependant ROS 1 Packages.
The rest of the relevant chapters 6 to 15 provide a more detailed explanation on how to use 
the Turtlebot3 and its simulation and provides its own commands and tutorials to practice with.

2 The next step is to move the files we have provided you in the Google Drive folder into your
equivalent folders on your local computer. These are additional files we have created for the project
and also original Turtlebot3 files we have updated and will need to replace the old ones in your folders.

The list of files and their locations includes:
* home/multi_bot_with_tag.launch
* home/Final_Project_Controller.py
* home/aruco_marker.launch
* home/catkin_ws/src/turtlebot3_simulations/turtlebot3_gazebo/models/turtlebot3_waffle_with_tag/model.sdf
* home/catkin_ws/src/turtlebot3_simulations/turtlebot3_gazebo/models/turtlebot3_waffle_with_tag/model.config
* home/catkin_ws/src/turtlebot3_simulations/turtlebot3_gazebo/models/turtlebot3_waffle_with_tag/meshes/marker.dae
* home/catkin_ws/src/turtlebot3_simulations/turtlebot3_gazebo/models/turtlebot3_waffle_with_tag/materials/textures/tag.png
* home/catkin_ws/src/turtlebot3_simulations/turtlebot3_gazebo/models/turtlebot3_waffle_with_tag/materials/sripts/tag.material
* home/catkin_ws/src/turtlebot3_simulations/turtlebot3_gazebo/launch/spawn_sdf.launch

After moving files remember to perfom catkin_make.


## Deployment

To deploy on your local system follow these steps

In a new terminal start a roscore.
'''
roscore
'''

In another new terminal run the following command. It will launch the gazebo environment with the two 
turtlebots located at their intitial poses within the plaza. The model of Turtlebots being used is waffle.
'''
roslaunch multi_bot_with_tag.launch
'''

In another new terminal run the following command. This will load the marker tracker, the Aruco tag, which 
is attached to the Leader Turtlebot.
'''
roslaunch aruco_marker.launch markerId:=701 markerSize:=0.05
'''

In another new terminal run the following command. This will open up a view window showing what the 
Following Turtlebot sees as it moves through the environment by itself. As it is following the Leader 
the view will show the Leader Turtlebot and its tag info.
'''
rosrun image_view image_view image:=/aruco_single/result
'''

This step is optional. In another new terminal run the following command. This will provide the raw 
pose information from the aruco tag.
'''
rostopic echo /aruco_single/pose
'''

In another new terminal run the following command to run this python file. This is the main controller 
code that gets the Follower Turtlebot following the Leader.
'''
python Final_Project_Controller.py
'''

In another new terminal run the following command. This will bring up the controls to allow the user
to control the Leader Turtlebot and move it around the environment. For best results drive this Turtlebot 
in a non-erratic way and do not crash into any obstacles within the environment. A good example of this is 
shown in the submitted video we have provided as well.
'''
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
'''

Following the above instructions you should now be able to successfully run our project and have a Turtlebot 
following another Turtlebot in simulation.

An Optional Step:
Run the following command in a new terminal to bring up the camera view as seen from the Leader Turtlebot.
For you if prefer a 1st person view when driving.
'''
rosrun image_view image_view image:=/camera/rgb/image_raw/
'''

Notes:
* tb3_1 refers to the Leader Turtlebot with the attached Aruco Tag
* tb3_0 refers to the Follower Turtlebot


## Authors

* Prathyush Chatry 12584429
* Kyle Pereira 12930893
* Katie Powell 98125659


### Individual Contributions

Prathyush Chatry 33.33%
Kyle Pereira 33.33%
Katie Powell 33.33%


## Acknowledgments

* To our Tutor Maleen and the help he provided
* To the ROS wiki turtlesim tutorial pages (http://wiki.ros.org/turtlesim/Tutorials)
* To Robotis and their emanual especially the ROS 1 section chapters 6-15 (https://emanual.robotis.com/docs/en/platform/turtlebot3/setup/#setup)
* To this tutorial with getting the Aruco tags working (http://ros-developer.com/2017/04/23/aruco-ros/)
