# Pick_and_place_Chess_Baxter

### Description
This is a coursework deliverd by University of Glasgow, Robotics Foundation. This repository contains a set of Python scripts to simulate a chess game using a robot in ROS (Robot Operating System) with the Gazebo simulation environment. The chessboard, pieces, and a table are spawned in Gazebo, and the robot can pick and place the chess pieces on the board.

### Prerequisites
- ROS (Robot Operating System)
- Gazebo Simulator
- MoveIt! for motion planning
- tf (Transform) Library in ROS
- Baxter SDK (The scripts were specifically written for Baxter robot, but you can adapt them to other robot platforms)

### Project Structure
The main directory consists of two subdirectories:

- models: Contains the table, chessboard and chess piece models in SDF format for the Gazebo simulator.
- src: Contains the Python scripts that control the robot.

### Python Scripts in src
- delete_chessgame.py: Deletes the chess game environment, i.e., chessboard and pieces, from the Gazebo simulation.

- gazebo2tfframe.py: Extracts object poses from Gazebo and publishes corresponding transforms in the ROS tf tree.

- pick_and_place_moveit.py: Defines a class for controlling a robot arm and gripper using the MoveIt! library, including moving to start position, picking up and placing objects.

- spawn_chessboard.py: Spawns a chess game environment, i.e., a table, chessboard and pieces, in the Gazebo simulation. This script also utilizes pick_and_place_moveit.py to position the chess pieces on the board.

### Running the Scripts
To use these scripts, you need to have a ROS environment with Gazebo and MoveIt! installed.
Please run `catkin_make` and source your workspace.  
And run the following in separate terminals:

Terminal 1:
```
roslaunch baxter_gazebo baxter_world.launch
```
Terminal 2:
```
rosrun baxter_tools enable_robot.py -e
rosrun baxter_interface joint_trajectory_action_server.py
```
Terminal 3:
```
roslaunch baxter_moveit_config baxter_grippers.launch
```
Terminal 4:
```
rosrun chess_baxter spawn_chessboard.py
```
Terminal 5:
```
rosrun chess_baxter pick_and_plave_moveit.py
```
Terminal 6:
```
rosrun chess_baxter gazebo2tfframe.py
```

If you want to restart the game, run the command below:
```
rosrun chess_baxter delete_chessgame.py
```
