# 🛞 my_bot — Differential-Drive Robot Model in ROS 2 (URDF/xacro + Gazebo)

![ROS 2](https://img.shields.io/badge/ROS-2-22314E)
![Gazebo](https://img.shields.io/badge/Simulator-Gazebo%20Classic-orange)
![URDF](https://img.shields.io/badge/Model-URDF%20%2F%20xacro-blue)

A ROS 2 package that describes a two-wheeled differential-drive robot (chassis, two driven wheels, caster) in URDF/xacro, visualises it in RViz2, and drives it in Gazebo with the `gazebo_ros` diff-drive plugin.

## 📂 Package layout

| Path | Contents |
| :--- | :--- |
| `description/robot.urdf.xacro` | Top-level robot description |
| `description/robot_core.xacro` | Links and joints: `base_link`, `chassis`, left/right wheels (continuous joints), caster |
| `description/inertial_macros.xacro` | Inertia macros for box, cylinder and sphere links |
| `description/gazebo_control.xacro` | `libgazebo_ros_diff_drive.so` plugin (subscribes to `/cmd_vel`, publishes odometry) |
| `launch/rsp.launch.py` | Starts `robot_state_publisher` with the processed xacro |
| `launch/launch_sim.launch.py` | Starts Gazebo, `robot_state_publisher` and spawns the robot |
| `config/*.rviz` | RViz2 views of the robot |
| `worlds/empty.world` | Empty Gazebo world |

## ▶️ Build & run

```bash
cd ~/ros2_ws/src && git clone https://github.com/Challa200Santhosh/my_bot.git
cd ~/ros2_ws && colcon build --symlink-install && source install/setup.bash

ros2 launch my_bot launch_sim.launch.py            # Gazebo + robot
ros2 run teleop_twist_keyboard teleop_twist_keyboard   # drive it
rviz2 -d src/my_bot/config/view_bot_rviz.rviz       # view TF and model
```

For a complete SLAM + Nav2 navigation stack, see [Diff_Drive_Robot](https://github.com/Challa200Santhosh/Diff_Drive_Robot).

## 🙏 Credits

Built from the [Articulated Robotics](https://articulatedrobotics.xyz/) `my_bot` ROS 2 package template (Apache-2.0).

## 👤 Author

**Challa Santhosh** — Model-Based Design & Embedded AI Engineer  
[LinkedIn](https://www.linkedin.com/in/challa-santhosh-36693828a/) · [GitHub](https://github.com/Challa200Santhosh) · sschalla10@gmail.com
