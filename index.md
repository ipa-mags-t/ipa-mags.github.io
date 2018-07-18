

# 1.Overview
Rob@work mini is a simple demonstration and development platform for navigation strategies from Fraunhofer IPA.
The HW development of the rob@work mini is a development based on the open source robot TurtleBot and the data will be made open source here in the RoboPORT repository.
The vision of this Project is to create a user community around this robot, which will be able to build their own robots of this type - further developments of their robots will be mirrored back into into this project, to provide them to all. 
By an increasing demand from the community, it is planed  to provide this robot as a toolkit, delivered directly from the sub-manufacturers.

# 2. Controller Setup
The code for the base controller is based on the [turtlebot3_core example](https://github.com/ROBOTIS-GIT/OpenCR/tree/master/arduino/opencr_arduino/opencr/libraries/turtlebot3/examples/turtlebot3_waffle/turtlebot3_core) and the [turtlebot_friends example](https://github.com/ROBOTIS-GIT/OpenCR/tree/master/arduino/opencr_arduino/opencr/libraries/turtlebot3/examples/turtlebot3_friends/turtlebot3_mecanum) for mecanumwheels and uses the formulae from [this paper](http://research.ijcaonline.org/volume113/number3/pxc3901586.pdf) for calculating the kinematics ([Summary](http://robotsforroboticists.com/drive-kinematics/)).

The base controller code requires the [OpenCR Board by ROBOTIS](https://github.com/ROBOTIS-GIT/OpenCR/wiki) and is using the turtlebot3_core libraries to set up a ROS Node to communicate with a ROS Master. 

The code for the adapted turtlebot core can be found at the [IPA fork of the ROBOTIS repository](https://github.com/flg-vs/OpenCR/tree/7404d3b905f6fad9b289b8b85112ffdaecd22337/arduino/opencr_arduino/opencr/libraries/turtlebot3/examples/turtlebot3_friends/turtlebot3_mecanum_core) under /examples/turtlebot3_friends/turtlebot3_mecanum_core. It will be tried to feed this back to the main repositoriy to make this code available directly from the turtlebot & friends examples.

- Installation

Make sure to install the Arduino IDE and the OpenCR libraries by following [these Instructions](emanual.robotis.com/docs/en/platform/turtlebot3/opencr1_0_software_setup/). Then use the Arduino IDE to upload the turtlebot3_mecanum_core.ino file onto the OpenCR board.

- Usage

The OpenCR Board launches a ROS Node that can be connected to by using the
```
rosrun rosserial_python serial_node.py
```
command.

Once the ROS Node is connected, the OpenCR Board publishes and subscribes to various topics listed below:

- Published Topics

| Topic Name       | Type                           | Description |
| ---------------- | ------------------------------ | ----------- |
| `sensor_state`   | `turtlebot3_msgs::SensorState` |  |
| `version_info`   | `turtlebot3_msgs::VersionInfo` |  |
| `cmd_vel_rc100`  | `geometry_msgs::Twist`         |  |
| `odom`           | `nav_msgs::Odometry`           |  |
| `joint_states`   | `sensor_msgs::JointState`      |  |
| `battery_state`  | `sensor_msgs::BatteryState`    |  |
| `magnetic_field` | `sensor_msgs::MagneticField`   |  |

- Subscribed Topics

| Topic Name    | Type                     | Description |
| ------------- | ------------------------ | ----------- |
| `cmd_vel`     | `geometry_msgs::Twist`   | Used to command the motors of the robot |
| `sound`       | `turtlebot3_msgs::Sound` | Plays a set of predefined sounds on the OpenCR Board |
| `motor_power` | `std_msgs::Bool`         | Turns the motors on or off |
| `reset`       | `std_msgs::Empty`        | Resets the board |

- Configuration

The following code lines need to be modified in the [turtlebot3_mecanum_core_config.h](turtlebot3_mecanum_core_config.h) and  [turtlebot3_mecanum_core_motor_driver](turtlebot3_mecanum_core_motor_driver.h) files: 
_Note: you might also want to change the Topic names that the OpenCR Board subscribes and publishes. This can be done in the core file._

turtlebot3_mecanum_core_config.h
```
//the radius of the wheels
#define WHEEL_RADIUS                    0.1      // meter
//half the distance between the front left and front right wheel
#define WHEEL_SEPARATION_X              0.09    // meter
//half the distance between the front and the rear wheels
#define WHEEL_SEPARATION_Y              0.115     // meter
```

turtlebot3_mecanm_core_motor_driver.h
```
#define DXL_LEFT_REAR_ID                3       // ID of left rear motor
#define DXL_RIGHT_REAR_ID               4       // ID of right rear motor
#define DXL_LEFT_FRONT_ID     
1	// ID of left front motor
#define DXL_RIGHT_FRONT_ID		2       // ID of right front motor
#define BAUDRATE                        1000000 // baurd rate of Dynamixel
```

If you use other motors than the Dynamixel XM430-W210, you might need to change other parameters in the turtlebot3_mecanum_core_motor_driver.h file as well.

# 3. Hardware Setup

- Motor Configuration

The motors used in this setup are Dynamixel XM430-W210. For the use in with the rob@work mini, the default configuration of these motors needs to be changed. This can be done by using one of the ROBOTIS configuration tools, one example is the DynamixelSDK which is available from the ROBOTIS Arduino examples. There, the different example programs can be uploaded to the OpenCR board to change the configuration of the motors.
It is important that during the configuration always only one motor is connected to the board. 
The motors need to be set to their correct ID, the ID configuration can be changed as shown in section 2. The default ID configuration is as follows:


| ID | Motor       | 
| -- | ----------- | 
| 1  | front left  | 
| 2  | front right | 
| 3  | rear left   | 
| 4  | rear right  | 

These IDs need to be set for the motors alongside the baudrate which needs to be set to 1000000. Additionally, the motors need to be set to `wheel mode`. Note: some of the example files from the DynamixelSDK set the mode to `joint mode` by default.

# 4. Robot Software Setup
This section describes the setup for the IPA in-house developed navigation and localization software. However, the robot can be used with open source software by publishing and subscribing to the topics described in section 2.
The following steps need to be taken in order to use the robot hardware with the latest IPA navigation software. 

1. Make sure that the most up-to-date ipa-navigation software is installed on the computer that is controlling the robot and that the correct license files are installed.
2. Set the ROBOT environment variable to `raw-mini`. If the navigation is also used the ROBOT_ENV variable needs to be set.
3. Use the `roslaunch cob_bringup robot.launch` terminal command to start the robot. Now it should already be possible to drive the robot using the joystick.
_If no navigation and localisation should be used, the setup is now finished_
4. If the navigation and localisation should be used. Now is the time to do a first mapping of the area. This is done by going into the environment folder that is set in the ROBOT_ENV variable. Then start the gmapping tool needs to be started. The documentation for this tool can be found [here](wiki.ros.org/gmapping). While mapping the environment, the robot should be driven around the whole area using the joystick. 
Once finished, end the gmapping tool and the map should be saved as map.pgm file.
5. Start the ipa navigation by using the `roslaunch ipa_navigation ipa_navigation.launch use_lts=true init_from_static_map=true`
6. Now the setup should be complete and the robot should be able to receive goals send via rviz or via the `/move_base_simple/goal` topic and drive there autonomously.

- Robot Upstart

For automatically launching the robot on startup, the [robot upstart](http://wiki.ros.org/robot_upstart) package can be used. This needs to be installed as instruced on the documentation page. It is advised that a custom launch file is created that already contains all necessary arguments and variables such as ROBOT and ROBOT_ENV since when starting up, robot upstart uses a different user to launch the applications and cannot use the variables stored in the `~/.bashrc` file.

# 5. Debugging

- Motors

For debugging the motors the [RoboPlus Manager 2.0](http://www.robotis.us/roboplus2/) application can be used. To use this software, either the [Usb2Dynamixel](http://www.robotis-shop-en.com/?act=shop_en.goods_view&GS=1289&GC=GD0B0107) adapter or the OpenCR board ([using this code](https://github.com/ROBOTIS-GIT/OpenCR/blob/develop/arduino/opencr_arduino/opencr/libraries/OpenCR/examples/10.%20Etc/usb_to_dxl/usb_to_dxl.ino)) needs to be connected.
Make sure that only one motor is connected to the board while running the initialization software.

If you have problems detecting the OpenCR board under Windows make sure that the correct drivers are installed for the STM32 chip. ([more infos here](http://forum.espruino.com/conversations/290299/))
