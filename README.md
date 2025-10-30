# Human-Following TurtleBot 3 with Gesture Recognition
This repository contains the implementation of a human-following robot using the TurtleBot 3 Burger, equipped with a Logitech c505e camera (or Raspberry Pi Camera Module v2/v3) for vision-based tracking and gesture recognition. The robot follows a human while maintaining a safe distance and responds to simple hand gestures (e.g., "stop," "go," "turn") to control its behavior. The project emphasizes human-robot interaction (HRI) with a research focus on evaluating gesture recognition accuracy. Developed as a two-semester project (September 2025–May 2026), it includes simulation in Gazebo and real-world testing. Hardware

## Project Overview
This repository contains the implementation of a human-following robot using the TurtleBot 3 Burger, equipped with a Logitech c505e camera (or Raspberry Pi Camera Module v2/v3) for vision-based tracking and gesture recognition. The robot follows a human while maintaining a safe distance and responds to simple hand gestures (e.g., "stop," "go," "turn") to control its behavior. The project emphasizes human-robot interaction (HRI) with a research focus on evaluating gesture recognition accuracy. Developed as a two-semester project (September 2025–May 2026), it includes simulation in Gazebo and real-world testing.
Hardware

* TurtleBot 3 Burger: Equipped with Raspberry Pi 4, OpenCR board, motors, battery, IMU, and wheel encoders.
* Camera: Logitech c505e USB webcam or Raspberry Pi Camera Module v2/v3 (~$25-35) mounted on the front plate.
* Optional Add-ons:
  * USB microphone (~$10) for potential future audio extensions.
  * Low-cost servo (~$5) for camera angle adjustment if needed.



## Software

1. ROS 2 Jazzy: Framework for robot control and communication.
2. Python 3: Primary programming language for scripts and nodes.
3. OpenCV: For human detection and tracking (e.g., color-based or cascade classifiers).
4. MediaPipe: For gesture recognition (hand landmark detection).
5. Gazebo: Simulation environment for prototyping and testing.
6. RViz: Visualization tool for debugging and monitoring.
7. TensorFlow Lite: Lightweight ML for gesture recognition (used in later phases).
8. Jupyter: For data analysis and visualization during evaluation.
9. Matplotlib: For plotting performance metrics.
10. Git: Version control for collaborative development.

## Installation

1. Hardware Setup:
* Assemble the TurtleBot 3 Burger per the official e-Manual.
* Mount the camera on the front plate.
* Connect and test all hardware components (motors, IMU, encoders).


2. Software Setup:

* Install ROS 2 Jazzy on the Raspberry Pi 4 and workstations. Follow the ROS 2 installation guide.
* Install dependencies:sudo apt update
```bash
sudo apt install python3-opencv python3-pip
pip3 install mediapipe tensorflow
sudo apt install ros-jazzy-turtlebot3 ros-jazzy-turtlebot3-msgs
```

* Set up ROS networking for SSH/remote control (ensure stable Ethernet or Wi-Fi).
* Install Gazebo:sudo apt install ros-jazzy-gazebo-ros-pkgs




3.  Repository Setup:

* Clone this repository: 
```bash
git clone https://github.com/TFelbor/Research-and-Development-Project.git
```

* Build the ROS workspace:
```bash
cd Research-and-Development-Project
colcon build
source install/setup.bash
```




## Usage

1. Teleoperation Test:
* Verify hardware functionality:
```bash
ros2 run turtlebot3_teleop teleop_keyboard
```
* Ensure the camera streams correctly:
```bash
ros2 run image_transport republish --ros-args --remap /image_raw:=/camera/image_raw
```

2. Simulation:
* Launch Gazebo simulation:

```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
* Test human-following in simulation before physical deployment.

3. Running the Prototype:
* Launch the human-following node (after prototyping phase):
```bash
ros2 run human_following follow_person
```
* Gesture recognition (post-January 2026):
```bash
ros2 run gesture_recognition gesture_control
```

## Project Roadmap

* Phase 1 (Sep 2025): Hardware assembly, ROS 2 setup, and teleoperation.
* Phase 2 (Oct–Dec 2025): Human-following prototype with camera-based tracking, Gazebo simulation, and basic safety stops.
* Phase 3 (Jan–Mar 2026): Gesture recognition integration (e.g., stop/go/turn), PID tuning, and initial user studies.
* Phase 4 (Apr–May 2026): Extensive testing, gesture accuracy evaluation, and final report/thesis.

## Contributing

* Use Git branches for features (e.g., feature/human-tracking, feature/gesture-recognition).
* Document code and experiments thoroughly.
* Log issues and metrics in the repository's Issues tab.

## Challenges and Notes

* Network Stability: Use Ethernet for reliable ROS communication.
* Lighting Conditions: Test vision algorithms in varied environments.
* Compute Limits: Offload heavy ML tasks to simulation or workstation if Raspberry Pi struggles.
* Backups: Regularly back up code and ROS bag data.

## Resources

* TurtleBot 3 e-Manual
* ROS 2 Jazzy Documentation
* MediaPipe Guide
* OpenCV Tutorials


