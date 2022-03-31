# Instructions

> This SDK is only applicable to the LiDAR products sold by Shenzhen LDROBOT Co., LTD. The product models are :
> - LDROBOT LiDAR LD06
> - LDROBOT LiDAR LD19
## 0. get LiDAR ROS2 Package
```bash
$ cd ~

$ mkdir -p ldlidar_ros2_ws/src

$ cd ldlidar_ros2_ws/src

$ git clone  https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2.git
# or
$ git clone  https://gitee.com/ldrobotSensorTeam/ldlidar_stl_ros2.git
```
## step 1: system setup
- Connect the LiDAR to your system motherboard via an onboard serial port or usB-to-serial module (for example, CP2102 module).

- Set the -x permission for the serial port device mounted by the radar in the system (for example, /dev/ttyUSB0)

  - In actual use, the LiDAR can be set according to the actual mounted status of your system, you can use 'ls -l /dev' command to view.

``` bash
$ cd ~/ldlidar_ros2_ws

$ sudo chmod 777 /dev/ttyUSB0
```
- Modify the `port_name` value in the Lanuch file corresponding to the radar product model under `launch/`, using `ld06.launch.py` as an example, as shown below.

```py
#!/usr/bin/env python3
from launch import LaunchDescription
from launch_ros.actions import Node

def generate_launch_description():
  return LaunchDescription([
    Node(
      package='ldlidar_stl_ros2',
      executable='ldlidar_stl_ros2_node',
      name='LD06',
      output='screen',
      parameters=[
        {'product_name': 'LDLiDAR_LD06'},
        {'topic_name': 'LiDAR/LD06'},
        {'port_name': '/dev/ttyUSB0'},
        {'frame_id': 'lidar_frame'}
      ]
    )
  ])
```

## step 2: build

Run the following command.

```bash
$ cd ~/ldlidar_ros2_ws

$ colcon build
```
## step 3: run

```bash
$ source install/setup.bash
```
- The product is LDROBOT LiDAR LD06

  ``` bash
  $ ros2 launch ldlidar_stl_ros2 ld06.launch.py
  ```
- The product is LDROBOT LiDAR LD19
  ``` bash
  $ ros2 launch ldlidar_stl_ros2 ld19.launch.py
  ```

## step 3: test

> The code supports ubuntu 20.04 ros2 foxy version and above, using rviz2 visualization.

- new a terminal (Ctrl + Alt + T) and use Rviz2 tool(run command: `rviz2`) ,open the `ldlidar.rviz` file below the rviz2 folder of the readme file directory
```bash
$ rviz2
```

| Product:          | Fixed Frame: | Topic:        |
| ------------------ | ------------ | ------------- |
| LDROBOT LiDAR LD06 | lidar_frame  | /LiDAR/LD06   |
| LDROBOT LiDAR LD19 | lidar_frame  | /LiDAR/LD19   |
