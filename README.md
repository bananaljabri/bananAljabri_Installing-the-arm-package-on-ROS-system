# bananAljabri_Installing-the-arm-package-on-ROS-system

1-	Download Oracle Virtual Machine 

If we want download ROS system on windows computer thus brings a lot of problems, for that we download virtual Box that enable us install ROS system by easy way.

Download from this link : https://www.virtualbox.org/
 
 ![image](https://user-images.githubusercontent.com/81714161/130367382-f8298601-64f9-4f0a-bfd2-41d62e672899.png)

 
2-	Download UBUNTU 18.04.5

Ubuntu is a Linux distribution based on Debian and composed mostly of free and open-source software.

Download from this link : https://releases.ubuntu.com/18.04.5/

3-	Install and run a UBUNTU on Virtual Machine
  
  ![image](https://user-images.githubusercontent.com/81714161/130367399-e4af6184-d047-433d-9e85-f4e80604e882.png)

 ![image](https://user-images.githubusercontent.com/81714161/130367444-2d410855-6f9b-41a4-9d53-280186ec8dfa.png)


4-	Download ROS MELODIC

From this link : http://wiki.ros.org/melodic/Installation/Ubuntu

Then follow this steps on cmd  terminal 

•	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

•	sudo apt install curl

•	curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

•	sudo apt-get update

•	sudo apt install ros-melodic-desktop-full

•	apt search ros-melodic

•	echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc

•	source ~/.bashrc

•	sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

•	sudo apt install python-rosdep

•	sudo rosdep init

•	rosdep update


5-	set a password

![image](https://user-images.githubusercontent.com/81714161/130367455-5adaa04c-c1c9-4775-a215-884ad85ba743.png)

 
6-	 Install a Catkin Workspace which is a folder to combine all packages for ROS.

•	sudo apt-get install ros-melodic-catkin

•	mkdir -p ~/catkin_ws/src

•	cd ~/catkin_ws/

•	catkin_make

•	cd ~/catkin_ws/src

•	git clone https://github.com/smart-methods/arduino_robot_arm.git we will use the arm from SM to work with.

•	cd ~/catkin_ws

•	rosdep install --from-paths src --ignore-src -r -y

•	sudo apt-get install ros-melodic-moveit

•	sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui

•	sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher

•	sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control

•	open a file (bashrc) : sudo nano ~/.bashrc.

•	At the end of the file add the follwing linesource /home/banan/catkin_ws/devel/setup.bash then press ctrl + o, (Note that banan is my ubuntu username).

•	source ~/.bashrc

•	To lunch the Rviz simulator with slider motors control (joint_state_publisher) use this command roslaunch robot_arm_pkg check_motors.launch

•	Rviz Simulator:

![image](https://user-images.githubusercontent.com/81714161/130367499-783cbb4d-b90d-444a-a030-2645fbd41df2.png)


 
7-	To control the robot arm physically if you need, connect the circuit diagram with your arm and the install Arduino IDE and ros_lib.

•	  Install Arduino IDE software wget https://downloads.arduino.cc/arduino-1.8.12-linux64.tar.xz then tar -xvf arduino-1.8.12-linux64.tar.xz then cd arduino-1.8.12/ then sudo ./install.sh

•	Download rosserial to communicate with arduino using the following commands sudo apt-get install ros-melodic-rosserial-arduino then sudo apt-get install ros-melodic-rosserial

•	Download ros_lib on arduino software using the following commands cd Arduino/libraries then rm -rf ros_lib then rosrun rosserial_arduino make_libraries.py .

•	To upload the Arduino code, select the Arduino port to be used on Ubuntu system, then we need to change the permissions (it might be ttyACM) by ls -l /dev |grep ttyUSB then sudo chmod -R 777 /dev/ttyUSB0 then upload the code from Arduino IDE

•	Run Rviz roslaunch robot_arm_pkg check_motors.launch rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200


8-	 Control the Arm in Gazebo simulator (real simulation).

•	Change the permission cd catkin/src/arduino_robot_arm/robot_arm_pkg/scripts then sudo chmod +x joint_states_to_gazebo.py

•	Open new terminal to launch Rviz roslaunch robot_arm_pkg check_motors.launch

•	Open new terminal to launch Gazebo roslaunch robot_arm_pkg check_motors_gazebo.launch

•	Then run the python script to communicate with Gazebo rosrun robot_arm_pkg joint_states_to_gazebo.py

•	Rviz with Gazebo:

![image](https://user-images.githubusercontent.com/81714161/130367530-b416183f-ffdf-4735-943e-a17dfe89607f.png)

 

9-	Now, lets used Moveit in Rvis which will help for kinematics, motion planning, trajectory processing and controlling the robot

•	roslaunch moveit_pkg demo.launch
 

10-	You may encounter many errors during the installation process, these links helped me:

•	https://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages

•	https://appuals.com/fix-unable-correct-problems-held-broken-packages/

