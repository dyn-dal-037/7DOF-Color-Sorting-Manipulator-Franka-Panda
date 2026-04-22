# Franka Panda Color Sorting Robot (ROS 2)

An autonomous manipulation project capable of identifying, picking, and sorting objects based on their color. This framework integrates the Franka Emika Panda robot with **MoveIt 2** for motion planning and **OpenCV** for visual perception within a Gazebo simulation.

## 🚀 Features

* **Autonomous Color Sorting:** Detects objects (Red, Green, Blue) and sorts them into specific bins.
* **Computer Vision Pipeline:** Real-time color thresholding and centroid detection using `panda_vision`.
* **Smart Manipulation:** Dynamic pick-and-place logic using the `pymoveit2` wrapper for precise end-effector control.
* **Gazebo Simulation:** Custom world environment with conveyor belts, bins, and colored debris.
* **Modular ROS 2 Architecture:** Decoupled nodes for perception, control, and description.

## 📂 Project Structure

* **`panda_bringup`**: Launch files to start the simulation, MoveIt 2, and the controller simultaneously.
* **`panda_controller`**: Contains the logic for the sorting state machine (Pick -> Move -> Sort -> Place).
* **`panda_vision`**: The vision node that subscribes to the camera feed and publishes object coordinates.
* **`panda_description`**: URDF models, meshes, and the specific Gazebo world for the sorting task.
* **`panda_moveit`**: MoveIt 2 configuration packages (SRDF, kinematics, joint limits).
* **`pymoveit2`**: A helper library used to simplify MoveIt 2 Python API calls.

## 🛠️ Installation

### Prerequisites
* **OS:** Ubuntu 22.04 LTS (Jammy Jellyfish)
* **ROS Distro:** ROS 2 Humble Hawksbill
* **Dependencies:** MoveIt 2, Gazebo, OpenCV, `cv_bridge`

### Build Instructions

1.  **Setup Workspace**
    ```bash
    mkdir -p ~/ros2_ws/src
    cd ~/ros2_ws/src
    ```

2.  **Clone Repository**
    ```bash
    git clone https://github.com/dyn-dal-037/7DOF-Color-Sorting-Manipulator-Franka-Panda.git .
    ```

3.  **Install Dependencies**
    ```bash
    cd ~/ros2_ws
    rosdep install --from-paths src --ignore-src -r -y
    ```

4.  **Build**
    ```bash
    colcon build
    source install/setup.bash
    ```

## 🎮 Usage

### 1. Launch the Simulation
Start the Gazebo world, Robot State Publisher, and RViz:
```bash
ros2 launch panda_bringup pick_and_place.launch.py
```

## Start the Sorting Task
In a new terminal, run the controller to begin the sorting loop:

```bash

ros2 run panda_controller pick_and_place_node
```
## 🤝 Inspiration
It is inspired my Manipulation projects by MechaMind Labs.

