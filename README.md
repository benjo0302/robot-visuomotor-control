# robot-visuomotor-control
ReadMe File

A ros python program to catch a flying ball thrown at a certain velocity and direction 
above the robot

Rospy is a python library for ros. In this program URSIM is setup
Open URSIM with admin privileges
cd ~/ursim-3.15.4.106291 Open a directory
"sudo ./start-ursim.sh" UR10 open with admin priviledges then close all error messages and program after it finishes loading

"./start-ursim.sh UR10" reopen normally in same directory

------------------------------------------------------------------------------------------

In a new terminal (control + shift + T) 

"roslaunch robot_control_simulation ur_robot_drivers.launch" ensure the IP address of the launch file matches the robot's IP

------------------------------------------------------------------------------------------

In a new terminal 

"rosrun robot_control_simulation ball_traj" run the ball trajectory to be able to send position signals to your code


------------------------------------------------------------------------------------------

In a new terminal

"/catkin_ws/src/robot_control_simulation/scripts" in this directory run "python3 mycode"

The code starts running....

The robot starts to move to home position and at home position 
Cartesian and orientational error is printed as well as if ball was caught or not

A few functions were used from from control library(control_lib.py):
•	Get_pose(self) – returns the position of the end effector. 
•	check_errors(self, robot_pose) – waits for ball position service and get error differences from end effector
•	convert_to_euler(self, quat) – take quaternion and convert it into x y z 
•	generate_move_l(self, pose)¬ – returns command to generate a linear movement along an axis
•	generate_move_j(self, waypoint, sequence = False, pose_msg = False)¬ – use waypoint list [x,y,z,rx,ry,rz] to generate a move command
•	rotate_tool(self, rx, ry, rz): function that rotates using tool frame instead of base frame in each axis or multiple axes.
•	move_j_pose(pose): function for joint movement to pose location.
•	move_x_error(value) , move_y_error(value), move_z_error(value) = definition for movement on each axis to return errors, value being the measure of movement(mm)
•	rotate_roll_error(value),rotate_pitch_error(value),rotate_yaw_error(value) = definition for rotation on each axis to return errors, value being the measure of movement(degrees)

The code ends when errors.ee_trans_error < 0.05 and errors.ee_rot_error < 5.
	
			
