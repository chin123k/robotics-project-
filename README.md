# Build

```bash
cd ~/ros2_ws
colcon build --packages-select indoor_robot
```

# Source workspace

```bash
source install/setup.bash
```

# Add to bashrc for convenience

```bash
echo "source ~/ros2_ws/install/setup.bash" >> ~/.bashrc
```

## 🚀 Quick Start

### Option A: Autonomous Navigation (Recommended)

**Terminal 1 - Simulation:**

```bash
cd ~/ros2_ws
source install/setup.bash
ros2 launch indoor_robot gazebo.launch.py
```

Wait for Gazebo to fully load (~10 seconds)

**Terminal 2 - Navigation:**

```bash
source install/setup.bash
ros2 launch nav2_bringup bringup_launch.py \
  use_sim_time:=True \
  autostart:=True \
  map:=$(ros2 pkg prefix indoor_robot)/share/indoor_robot/maps/warehouse_map.yaml \
  params_file:=$(ros2 pkg prefix indoor_robot)/share/indoor_robot/config/nav2_params.yaml
```

**Terminal 3 - Visualization:**

```bash
source install/setup.bash
ros2 launch nav2_bringup rviz_launch.py
```

In RViz:

- Click "2D Pose Estimate" (top toolbar)
- Click on map where robot is in Gazebo, drag to set orientation
- Click "Nav2 Goal" (top toolbar)
- Click destination → Robot navigates autonomously! 🎉

### Option B: Manual Mapping (Create New Map)

**Terminal 1 - Simulation:**

```bash
ros2 launch indoor_robot gazebo.launch.py
```

**Terminal 2 - SLAM:**

```bash
ros2 launch indoor_robot slam.launch.py
```

**Terminal 3 - Manual Control:**

```bash
cd ~/ros2_ws/src/indoor_robot/scripts
python3 simple_control.py
```

Use W/A/S/D keys to drive, Space to stop, Q to quit

**Terminal 4 - Save Map (after exploring):**

```bash
cd ~/ros2_ws/src/indoor_robot/maps
ros2 run nav2_map_server map_saver_cli -f my_new_map
```
