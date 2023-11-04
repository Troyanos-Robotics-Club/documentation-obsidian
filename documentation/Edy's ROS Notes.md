---
topic: robotics, programming, python, c++
tags:
  - documentation
description: Notas personales de Edy
---
# TLDR [[ROS]]

ROS es un sistema para comunicación entre robots. Es muy útil para controlarlos y ya tiene muchas librerías incluidas.

**Purpose:** Para la escuela y proyectos personales, poder controlar robots es muy útil

# Introduction & Setup

_Explain where you are getting the information_

# Templaets for Ros2

[Templates](https://github.com/ros2/examples)

# Introduction

- ROS es open source
- Robotics developer for scaling system

## Environment

- Humble ROS 2 (look at the doc)

# Intro to ROS2

- Framework
    - Data Distribution Service
        - Communication throuhg all nodes
    - Nodes
        - Code that can acces de DDS


- Methods of communication in nodes
    - Publisher | subscriber (unidirectional)
        - Sub to topic
        - Send messages
    - Services
        - Client - Server
        - Request | Response
    - Action
        - Send a goal to a service
        - Service constantly sends updates on the status (feedback)
        - When the goal is reach, then you send a Result
- Node can have parameters to configure for variables (change by user or nodes)
- Bag files (record the data) (playback)
- Packages
    - Contain code functionallity and distributed
- Cross platform support
    - Windows / Mac / Ubunut (not that good yet)
    - Compatible with ROS 1

## ROS 1 Vs ROS 2

ROS 2 is a newer version of ROS that has several key differences from ROS 1, including:

- **Scalability**: ROS 2 is designed to be more scalable than ROS 1, meaning that it can handle larger and more complex robotic systems.
- **Real-time performance**: ROS 2 has been designed with real-time performance in mind, making it more suitable for safety-critical applications.
- **Security**: ROS 2 includes built-in security features, such as encryption, to help protect robotic systems from attacks.
- **Cross-platform support**: ROS 2 is designed to be more cross-platform than ROS 1, with support for Windows, Mac, and Ubuntu.
- **Better communication**: ROS 2 uses a more efficient and flexible communication system called Data Distribution Service (DDS) that allows for better communication between nodes.

# ROS Workspace

The file structure of the ROS2 workspace is as follows:

```
~/ros2_ws
├── build
│   ├── beginner_tutorials
│   ├── hello_world
│   ├── my_robot
│   ├── project_1
│   ├── project_2
│   └── tutorial_msgs
├── install
│   ├── bin
│   ├── lib
│   └── share
└── src
    ├── beginner_tutorials
    ├── hello_world
    ├── my_robot
    ├── project_1
    ├── project_2
    └── tutorial_msgs

```

- Ros workspace
    - src
        - package_name
            - scripts (python)
                - **init**.py
                - your_ros_sript.py
            - src (c++)
            - launch
            - msg
            - package.xml (auto)
            - CMakeList (auto)
    - build (auto)
    - install (auto)
    - log (auto)

<aside>
💡 You make the workspace, but the package you auto generated it
</aside>

```python
ros2 pkg create udemy_ros2_pkg --built-type ammet_cmake
```

> [!important] Where to run Colcon build
> colcon build in workspace to build everythong

## Nodes


<aside>
💡 Puedes usar un topic echo para poner las cosas

</aside>


## Configuring Packages

Cmake:

```

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rclpy REQUIRED)

ament_python_install_package(scripts)

install(PROGRAMS
    scripts/publisher.py
    scripts/subscriber.py
    DESTINATION lib/${PROJECT_NAME}
)
```

Package.xml: Pon las dependecias

```xml
<buildtool_depend>ament_cmake</buildtool_depend>
    <buildtool_depend>ament_cmake_python</buildtool_depend>
    <depend>rclpy</depend>
```

<aside>
💡 Debes de poner el shbang en cada uno

</aside>

```
❯  ros2 pkg executables udemy_ros2_pkg
```

<aside>
💡 Puedes construir el paquete con ament_python, la desventaja es que no puedes agregar el cpp code despues

</aside>

<aside>
💡 Use colcon build —sym-install to link it

</aside>

<aside>
💡 IN vscode, you can make a task that can run

</aside>

```bash
#!/bin/bash

# Python env
source ~/Documents/aprendizaje/ros/ros-workspaces/ros2_py_ws/venv/bin/activate
# ROS env
source /opt/ros/humble/setup.bash
# Colon cmd
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
# Workspace
# source ~/Documents/aprendizaje/ros/ros_ws/install/setup.bash
source ~/Documents/aprendizaje/ros/ros-workspaces/ros2_py_ws/install/setup.bash
echo "Loaded ROS env successfully"

rm -rf build/ install/ log/

colcon build --symlink-install && find . -wholename './src/*.py' -exec chmod +x {} \;
```

# Interfaces

<aside>
💡 std_msgs library is useful to know what it is used for

</aside>

[std_msgs Message / Service / Action Documentation](https://docs.ros2.org/foxy/api/std_msgs/index-msg.html)

<aside>
💡 There are many more including for lidar, baterry, joycon etc

</aside>

[sensor_msgs - ROS Wiki](http://wiki.ros.org/sensor_msgs)


# Proj # 1


## Node Parameters

<aside>
💡 Dinamic variables for nodes

</aside>

<aside>
💡 ros2 param list , ros2 param get <param>, ros2 param describe, set

</aside>

```python
self.declare_parameter("wheel_radius", WHEEL_RADIUS_DEFAULT)
print(self.get_parameter("wheel_radius").value())
```


# Launch Files

<aside>
💡 Put it in a package, and then you can launch it. Some modifications in cmake to make it work. Analogous to docker-compose

</aside>

```python
from launch import LaunchDescription
from launch.actions import ExecuteProcess
from launch_ros.actions import Node

def generate_launch_description():
    return LaunchDescription(
        [
            Node(
                package="udemy_ros2_pkg",
                executable="rpm_pub.py",
                name="rpm_pub_node",
            ),
            ExecuteProcess(
                cmd=["ros2", "topic", "list"],
                output="screen",
            ),
        ]
    )
```

# Services

> [!tldr] Server client architecture
> Service interfaces as a a client-server architecture. So a node request something and that service returns it

```sh
ros2 interface list
```

Nos enseña las interfaces. Luego con el `show` puedes ver las interfaces

```text
bool data # e.g. for hardware enabling / disabling
---
bool success   # indicate successful run of triggered service
string message # informational, e.g. for error messages
```

Esto es lo que sale el _request_ y abajo es el _response_

Para hacer un service:

```
-src
-srv
	- interface.srv
```

Dentro del package

```c
int64 number
---
string decision
```

Esto define lo que es un servicio

```xml
    <buildtool_depend>rosidl_default_generators</buildtool_depend> <exec_depend>rosidl_default_runtime</exec_depend>
    <member_of_group>rosidl_interface_packages</member_of_group>

```

Estas dependencias para que funcionen

```python
class OddEvenCheckServer(Node):
    def __init__(self):
        super().__init__("odd_even_service_server_node")
        self.srv = self.create_service(
            OddEvenCheck, "odd_even_check", self.determine_odd_even
        )

    def determine_odd_even(self, request, response):
        print("Request Received")

        if request.number % 2 == 0:
            response.decision = "Even"
        elif request.number % 2 == 1:
            response.decision = "Odd"
        else:
            response.decision = "Error"

        print(request)
        print(response)

        return response

```

This is a service and a client

> [!important] Add them as if they were nodes to actually use them

```python
class OddEvenCheckClient(Node):
    def __init__(self):
        super().__init__("odd_even_client_node")
        self.client = self.create_client(OddEvenCheck, "odd_even_check")
        self.req = OddEvenCheck.Request()

    def send_request(self, num):
        self.req.number = int(num)
        self.client.wait_for_service()
        self.future = self.client.call_async(self.req)
        rclpy.spin_until_future_complete(self, self.future)

        self.result = self.future.result()
        return self.result

```

The services uses futures to handle the results, so you need to spin until future is complete

> [!note] Vscode has a nice extension for ROS2

```sh
ros2 service list
ros2 service call /service-path
```

```sh
$ ros2 service call /odd_even_check udemy_ros2_pkg/srv/OddEvenCheck number:\ 5\
requester: making request: udemy_ros2_pkg.srv.OddEvenCheck_Request(number=5)

response:
udemy_ros2_pkg.srv.OddEvenCheck_Response(decision='Odd')

```

# Proyecto 2 Servicio De Imagen

> [!todo] Image project
> Make a service that takes a request of a picture at a certain angle, then returns the image sent by a robot to the client

- [ ] Make service that takes a deg and returns an image
- [ ] Make a service that asks for a degree to the service and recieves an image
- [ ] (Optional) display the image in your computer

## CV2 and CV_Bridge

How to open an image in cv2

```python
import cv2
from cv_bridge import CvBridge

image = cv2.imread(file_location)

cv2.imshow("Display window name", image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## CV_Bridge

> [!info]- CV_Bridge Library
> CV_Bridge is a library that translate cv images to ros messages

```python
import cv2
from cv_bridge import CvBridge

image = cv2.imread(file_location)

# From image to ros
image_msg = CvBridge().cv2_to_imgmsg(image)

# From ros to image
image = CvBridge().imgmsg_to_cv2(image_msg)

```


## Solution

Remember to add this to have the messages

> [!important] Add this if you are using the sensor mesages package

```cmake
find_package(sensor_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
    "srv/OddEvenCheck.srv"
    "srv/TurnCamera.srv"
    DEPENDENCIES
    sensor_msgs
)

```

### Turn Image Service

```srv
float32 degree_turn
---
sensor_msgs/Image image

```

```sh
$ ros2 service call /turn_camera udemy_ros2_pkg/srv/TurnCamera degree_turn:\ 15.0\
```

Fuera de eso, es muy sencillo

# Actions

## Project Walkthrough

La diferencia entre Action y [[documentation/Edy's ROS Notes#Services|Service]] es que el servicio tiene un _request_ y una _response_. Las acciones tienen _goal_, _result_ y _feedback_

El _goal_ y _result_ son análogos a _request_ y una _response_, pero el feedback es un diferente tipo de respuesta.


### Steps Para Un Action

1. Hacer un archivo en `actions/` con terminación action (usa messages)

```text
# Goal
geometry_msgs/Point goal_poit

---

# Result
float32 elapsed_time

---

# Feedback
float32 current_distance

```

1. Update package.xml and add depency of actions_msg

```xml
    <depend>rclpy</depend>
    <depend>action_msgs</depend>
```

1. Add to rosidl_generate_interfacfe

```cmake
rosidl_generate_interfaces(${PROJECT_NAME}
    "srv/OddEvenCheck.srv"
    "srv/TurnCamera.srv"
    "action/Navigate.action" # Action
    DEPENDENCIES
    sensor_msgs geometry_msgs #Dependecy on geometyr msg
)
```

	### Action Server

```python
from rclpy.action import ActionServer
from udemy_ros2_pkg.action import Navigate

...

    def __init__(self):
        super().__init__("navigate_action_server")
        self._action_server = ActionServer(
            self, Navigate, "navigate", self.navigate_callback
        )

```

> [!NOTE] You can have internal pub's and sub's inside a node. But if you do this, remeber to properly destroy them

If you call spin within a spin, it can lead to getting stuck. Use the ok function to run

```python
while rclpy.ok():
	rclpy.spin(action_server)
```

> [!important] Instead of using "time.sleep" use "spin_once" to wait. Spin once stops the execution of the current node, but allows others to keep going

The callback controls the action, and it sends feedback to whomever is subscripbed. It usually _controlled by a action client_

```python
def __init__ ...
        self._action_server = ActionServer(
            self, Navigate, "navigate", self.navigate_callback
        )

    def navigate_callback(self, goal_handle: GoalEvent):
        print("Received Goal Request")
        robot_goal_point: Point_T = (
            goal_handle.request.goal_point.x,
            goal_handle.request.goal_point.y,
            goal_handle.request.goal_point.z,
        )
        start_time = self.get_clock().now().to_msg().sec
        print("Robot Goal Point: {}".format(robot_goal_point))

        # We do this for not having to block the execution
        while self._current_robot_position is None:
            print("Waiting for robot position data...")
            rclpy.spin_once(self, timeout_sec=3)

        distance = math.dist(self._current_robot_position, robot_goal_point)
        feedback_msg = Navigate.Feedback()

        while distance > DISTANCE_THRESHOLD:
            distance = math.dist(self._current_robot_position, robot_goal_point)

            # Feedback
            feedback_msg.current_distance = distance
            goal_handle.publish_feedback(feedback_msg)

            # This makes it to wait without blocking the execution of everything else
            rclpy.spin_once(self, timeout_sec=1)

        # Finish goal
        goal_handle.succeed()
        end_time = self.get_clock().now().to_msg().sec
        result = Navigate.Result()
        result.elapsed_time = float(end_time - start_time)

        return result
```

### Action Client

```python
from rclpy.action import ActionClient
```

```python
class NavigateActionClient(Node):
    def __init__(self):
        super().__init__("navigate_action_server")
        self._action_client = ActionClient(self, Navigate, "navigate")

    def send_goal(self, x: float, y: float, z: float):
        goal_msg = Navigate.Goal()
        goal_msg.goal_point.x = float(x)
        goal_msg.goal_point.y = float(y)
        goal_msg.goal_point.z = float(z)

        self._action_client.wait_for_server()
        self._send_goal_future = self._action_client.send_goal_async(
            goal_msg, feedback_callback=self.feedback_callback
        )
        self._send_goal_future.add_done_callback(self.done_callback)

    def feedback_callback(self, feedback_msg):
        feedback: float = feedback_msg.feedback
        print(f"Feedback received: {feedback} distance")

    def done_callback(self, future: rclpy.Future):
        goal_handle = future.result()

        if goal_handle is None:
            print("Goal rejected")
            return None

        if goal_handle.accepted == False:
            print("Goal rejected")
            return None

        print("Goal accepted")
        self.get_result_future = goal_handle.get_result_async()
        self._get_result_future.add_done_callback(self.get_result_callback)

        pass

    def get_result_callback(self, future: rclpy.Future):
        result = future.result().result
        print(f"Result: {result} seconds")
        rclpy.shutdown()
```

### Manually Sending to sub

```sh
ros2 topic pub --once <topic> "data"
```


# Additional Tools

[Ros index](https://index.ros.org/) for searching additional packages

Example:

- [USB cam](https://index.ros.org/p/usb_cam/github-ros-drivers-usb_cam/#humble) package for camera

> [!tip] To install packages for distro
> Run the command like this:
> ```sh
>  sudo apt install package-$ROS_DISTRO-name
> ```

# Bag Files

Review the history of ROS2

Command: `ros2 bag record`

- `-a` all topics
- `<topic>` only a topic
- `-o <folder>`

_Works like a interactive player_

Command; `ros2 bag info <folder>` show info

Command; `ros2 bag play -l <folder>` show replay topic in bags (simulate all the calls from all the topics)

It can replay info like this:

```txt
---
header:
  stamp:
    sec: 1569427458
    nanosec: 280378103
  frame_id: gps
twist:
  linear:
    x: 0.4576322589473745
    y: 0.6340561540067757
    z: 0.0
  angular:
    x: 0.0
    y: 0.0
    z: 0.0
---
header:
  stamp:
    sec: 1569427458
    nanosec: 328242063
  frame_id: gps
twist:
  linear:
    x: -0.7450832896236113
    y: -0.23728755211093305
    z: 0.0
  angular:
    x: 0.0
    y: 0.0
    z: 0.0

```

**You can set start times and edit bag files in ros, look for documentation **

## Visualization Tools

_Also on ros1_

### Rviz2

```sh
rviz2
```

> [!tldr] For Vizualizing Space Data
> E.g. Lidar data


### RQT

For vizualizing ros topics and stuff other stuff in real life (instead of the terminal)

You subscribe to stuff

**Message publisher** te permite poner mensajes de prueba

**Node graph plugin** == **rqt_graph**

So nice GUI

**Plot** plot data

**Images** Also you can record images

> [!NOTE] Puedes tener todo conlos comandos, pero este es el gui

# Ros2 Advanced Features

## ROS Networking

Works out of the box, but it is insecure

> [!todo] Both computers must be connected to the same router (wifi or ethernet)
> As I tried, also work if they are connected amongst them

Requirements:

- Same network (network and mask)

### Domains

It is a way to isolate a ROS2 project in the same network

[Documentation](https://docs.ros.org/en/foxy/Concepts/About-Domain-ID.html)

Set the domain:

```sh
export ROS_DOMAIN_ID=1
```

To connect, both must be in the same domain

## Security Features

### [SROS2 package](https://index.ros.org/p/sros2/github-ros2-sros2/#humble)

[Tutorial on security](https://docs.ros.org/en/humble/Tutorials/Advanced/Security/Introducing-ros2-security.html)

> [!tldr] Set it up in the tutorial, and it makes so that no one can listen to your topics

# [[Ignition]]

> [!danger] DO NOT OPEN GAZEBO WITH THE TILE MANAGER. IT CRASHES THE COMPUTER

## Ros Bridge

Compatibility with Ros1 and Ros2. Use it if you need it.

# Executors and Multithreading

> [!error] You cannot call services inside other services!
> This is because nested callbacks are not supported. Do not design stuff like that!
