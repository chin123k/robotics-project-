create a readmefile fr this text
don't add extra use same text
🤖 Indoor Navigation Robot (ROS 2)







🚀 Autonomous Indoor Robot Navigation using ROS 2 + Nav2 + Gazebo + RViz

🎥 Demo
🔹 Autonomous Navigation

🔹 SLAM Mapping

📌 Tip: Replace these with your actual GIFs (screen recordings from Gazebo + RViz)

📌 Overview

This project implements an indoor autonomous robot that can:

🧭 Navigate using a pre-built map
🗺️ Perform SLAM to create maps
🎮 Be manually controlled via keyboard
📍 Visualize everything in RViz
🤖 Use Nav2 stack for path planning & obstacle avoidance
🏗️ System Architecture

(Optional: add diagram later — I can generate one for you)

📦 Project Setup
🔧 Build Workspace
cd ~/ros2_ws
colcon build --packages-select indoor_robot
🔌 Source Workspace
source install/setup.bash
⚡ Add to .bashrc (Optional)
echo "source ~/ros2_ws/install/setup.bash" >> ~/.bashrc
🚀 Quick Start
🔹 Option A: Autonomous Navigation
🖥️ Terminal 1 — Simulation
cd ~/ros2_ws
source install/setup.bash
ros2 launch indoor_robot gazebo.launch.py

⏳ Wait ~10 seconds for Gazebo to load

🧠 Terminal 2 — Navigation
source install/setup.bash
ros2 launch nav2_bringup bringup_launch.py \
  use_sim_time:=True \
  autostart:=True \
  map:=$(ros2 pkg prefix indoor_robot)/share/indoor_robot/maps/warehouse_map.yaml \
  params_file:=$(ros2 pkg prefix indoor_robot)/share/indoor_robot/config/nav2_params.yaml
📊 Terminal 3 — RViz
source install/setup.bash
ros2 launch nav2_bringup rviz_launch.py
🎯 In RViz
Click "2D Pose Estimate" → Set robot position
Click "Nav2 Goal" → Select destination

🎉 Robot navigates autonomously!

🔹 Option B: Manual Mapping (SLAM)
🖥️ Terminal 1 — Simulation
ros2 launch indoor_robot gazebo.launch.py
🧠 Terminal 2 — SLAM
ros2 launch indoor_robot slam.launch.py
🎮 Terminal 3 — Manual Control
cd ~/ros2_ws/src/indoor_robot/scripts
python3 simple_control.py
Controls:
Key	Action
W	Forward
A	Left
S	Backward
D	Right
Space	Stop
Q	Quit
💾 Terminal 4 — Save Map
cd ~/ros2_ws/src/indoor_robot/maps
ros2 run nav2_map_server map_saver_cli -f my_new_map

📁 Output:

my_new_map.yaml
my_new_map.pgm
🧠 Features

✨ Autonomous Navigation (Nav2)
✨ SLAM-based Mapping
✨ Real-time Visualization (RViz)
✨ Manual Teleoperation
✨ Custom Map Saving
