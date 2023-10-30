# Virtual Machine ROS2 Setup


The newest currently supported ROS2 LTS distribution is Humble, which runs on Ubuntu 22.04. This distribution won’t reach EOL (end of life) until May 2027. The different ROS distributions can be found here: <https://docs.ros.org/en/rolling/Releases.html>

1. Creating a virtual machine with Ubuntu 22.04 (If already using a Linux computer, you may skip this step. Just make sure that the Ubuntu version running matches the ROS2 distribution that will be used. Ubuntu 22.04 is recommended to use the newest ROS2 distribution Humble)
   1. Installing VirtualBox
      1. Go to the following link: <https://www.virtualbox.org/>
      1. Download VirtualBox for your computer’s OS
      1. Open the executable file and complete the installation wizard
      1. Open the software once done
   1. Download the Ubuntu 22.04 LTS Desktop
      1. Go to the following link: <https://ubuntu.com/download/desktop>
      1. Download the file for Ubuntu 22.04 LTS Desktop
   1. Setting up the virtual machine configuration
      1. With VM open, click on *New*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.001.png)

1. Enter the name of the computer (it can be whatever you want).

Select the Folder (it can be the default Folder that appears).

Leave ISO Image as *not selected* for now.

On Type select *Linux*

On version select *Ubuntu (64-bit)*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.002.png)

1. Give the VM as much RAM and Processors as you can. This will help the software running be faster and easier to use. In this case I will assign about 10 GB of RAM and 3 CPUs.

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.003.png)


1. Assign the Memory the VM will have. 32 GB is sufficient

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.004.png)

1. Select Finish

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.005.png)

1. Choose the newly created VM and click on *settings*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.006.png)

1. Go to *Storage,* then click on *Empty,* then on the blue disk that appears to the right and select the Ubuntu 22.04 Image downloaded in step 1.2. If it is not recognized in the scroll down section that appears, go the folder where it is downloaded and select it

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.007.png)

1. Click *OK* and then *Start.* Anytime you want to change the configuration of the VM you can go to *Settings* and update it (Change RAM, Processors, etc.)
1. Recommended: If you have a single screen, it is easiest to work in the VM without the VirtualBox full-screen mode. To adjust the screen size, right click in the Ubuntu VM and select “Display Settings”. Here you can adjust the screen size. A recommended view of how it can look is the following:

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.008.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.009.png)






1. Ubuntu Setup
   1. Ubuntu Installation
      1. Select *Try or Install Ubuntu*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.010.png)






1. Select *Install Ubuntu*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.011.png)


1. Choose your Keyboard Layout and Continue

1. Proceed with *Normal Installation* and *Download updates while installing Ubuntu*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.012.png)

1. Select *Erase disk and install Ubuntu* (this is only for the VM, your computer’s Disk will remain untouched). Select continue on the pop up that appears
1. Choose your time zone and continue
1. Create the computer’s username and password and continue

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.013.png)

1. Wait while everything is installed

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.014.png)

1. Once the installation is complete, select *Restart Now* on the pop up that appears. Press *Enter* when asked
1. You may connect your online accounts or just press *Skip*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.015.png)




1. Select *Skip for now* and click *Next*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.016.png)

1. If a software updater appears, select *Remind me Later*

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.017.png)

1. You can choose to send system info or not, then click *Next*
1. Choose whether or not to use Location Services and then click *Next*








1. Tools and software needed
   1. VisualStudio Code
      1. From *Ubuntu Software* select to install Visual Studio Code and open it once finished

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.018.png)

1. Open VSCode (You may add a shortcut of VSCode to the side bar by right clicking the icon and selecting add to favorites)

Install the following extensions

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.019.png)

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.020.png)

![](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.021.png)

1. Open the terminal and enter the commands (each command is sent separately):

sudo apt update

sudo apt upgrade

sudo apt autoremove

Example:

![A screenshot of a computer Description automatically generated](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.022.png)

![A screenshot of a computer Description automatically generated](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.023.png)

![A screenshot of a computer Description automatically generated](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.024.png)

1. To install terminator enter the command:

sudo apt install terminator

This is a useful app that can have several terminals in a single screen. You can use CTRL+SHIFT+O to split the screen horizontally or CTRL+SHIFT+E to split the screen vertically. For more info go to the following link: <https://www.makeuseof.com/run-multiple-linux-terminals-with-terminator/?newsletter_popup=1>

![A screenshot of a computer Description automatically generated](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.025.png)

1. To install python3 pip enter the command:

sudo apt install python3-pip

1. To install git enter the command:

sudo apt install git

1. ROS2
   1. ROS2 installation (Steps taken from the official guide on <https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html>):
      1. Verify you have UTF-8

locale

1. Enter the following commands (DO NOT SKIP ANY COMMANDS!!):
- sudo apt install software-properties-common
- sudo add-apt-repository universe
- sudo apt update && sudo apt install curl -y
- sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
- echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU\_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

- sudo apt update
- sudo apt upgrade
- sudo apt install ros-humble-desktop
- sudo apt install ros-dev-tools
- cd
- source /opt/ros/humble/setup.bash && echo "source /opt/ros/humble/setup.bash" >> .bashrc

1. Python dependencies
- pip install --user -U empy pyros-genmsg setuptools

1. Install ROS2 build tool - colcon
- sudo apt install python3-colcon-common-extensions
- cd
- source /usr/share/colcon\_argcomplete/hook/colcon-argcomplete.bash && echo "source /usr/share/colcon\_argcomplete/hook/colcon-argcomplete.bash" >> .bashrc

1. Creating a ROS2 workspace
   1. Enter the following commands:
- cd
- mkdir -p ~/ros2\_ws /src/
- cd ~/ros2\_ws/src/
- git clone <https://github.com/davidogarzas/taller_ros2.git>
- cd ..
- source /opt/ros/humble/setup.bash
- colcon build
- cd
- source ~/ros2\_ws/install/setup.bash && echo "source ~/ros2\_ws/install/setup.bash" >> .bashrc

To see if everything was installed correctly, you may run the following commands in separate terminals (or different terminals in Terminator):

- ros2 run turtlesim turtlesim\_node
- ros2 run turtle3 manager
- ros2 run turtle3 movement
- ros2 run turtle3 spawner

![A screenshot of a computer screen Description automatically generated](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.026.png)

If everything works correctly, you should see a screen with a Turtle that chases down the other Turtles that appear on the screen.





**Troubleshooting:**

If something in the installation is wrong, check that the following is correct.

Type:

- cd
- gedit ~/.bashrc

Scroll down the file and check that it has these 3 lines in the end of the file:

- source /opt/ros/humble/setup.bash
- source ~/ros2\_ws/install/setup.bash
- source /usr/share/colcon\_argcomplete/hook/colcon-argcomplete.bash

![A screenshot of a computer Description automatically generated](Aspose.Words.58c94682-248e-4856-9434-7291b8c5d500.027.png)

If it doesn’t, add them and save the file. Close all terminals and open them again. Anytime an error occurs, doing this may solve the issue. Another option is to do:

- cd
- source .bashrc