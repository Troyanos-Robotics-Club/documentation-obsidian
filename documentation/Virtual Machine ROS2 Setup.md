
The newest currently supported ROS2 LTS distribution is Humble, which runs on Ubuntu 22.04. This distribution won’t reach EOL (end of life) until May 2027. The different ROS distributions can be found here: <https://docs.ros.org/en/rolling/Releases.html>

# Installing through VM

Creating a virtual machine with Ubuntu 22.04 (If already using a Linux computer, you may skip this step. Just make sure that the Ubuntu version running matches the ROS2 distribution that will be used. Ubuntu 22.04 is recommended to use the newest ROS2 distribution Humble)

## Installing Virtual Box

  1. Go to the following link: <https://www.virtualbox.org/>
  1. Download VirtualBox for your computer’s OS
  1. Open the executable file and complete the installation wizard
  1. Open the software once done

## Installing Ubuntu 22.04

   - Download the Ubuntu 22.04 LTS Desktop
      1. Go to the following link: <https://ubuntu.com/download/desktop>
      1. Download the file for Ubuntu 22.04 LTS Desktop
   - Setting up the virtual machine configuration
      1. With VM open, click on *New*

![[Pasted image 20231101103852.png]]

1. Enter the name of the computer (it can be whatever you want).
1. Select the Folder (it can be the default Folder that appears).
1. Leave ISO Image as *not selected* for now.
1. On Type select *Linux*
1. On version select *Ubuntu (64-bit)*

![[Pasted image 20231101103901.png]]

Give the **VM as much RAM and Processors as you can** (normally around 4GBs and 2~3 CPU is enough). This will help the software running be faster and easier to use. In this case I will assign about 10 GB of RAM and 3 CPUs.

![[Pasted image 20231101103906.png]]

Assign the Memory the VM will have. 32 GB is sufficient

![[Pasted image 20231101103911.png]]

Select Finish

![[Pasted image 20231101103915.png]]

Choose the newly created VM and click on *settings*

![[Pasted image 20231101103920.png]]

Go to *Storage,* then click on *Empty,* then on the blue disk that appears to the right and select the Ubuntu 22.04 Image downloaded in step 1.2. If it is not recognized in the scroll down section that appears, go the folder where it is downloaded and select it

![[Pasted image 20231101103925.png]]

Click *OK* and then *Start.* Anytime you want to change the configuration of the VM you can go to *Settings* and update it (Change RAM, Processors, etc.)

### Ubuntu Setup

When you have installed ubuntu, you can open the virtual machine and start with the installation process

- Ubuntu Installation
  - Select *Try or Install Ubuntu*

![[Pasted image 20231101103941.png]]

> [!tip]
> If the screen doesn't show the "Next", "Continue" or "Install" buttons, you can drag the Installation window right or left to show the buttons. 


Select *Install Ubuntu*

![[Pasted image 20231101103945.png]]

Choose your Keyboard Layout and Continue

Proceed with *Normal Installation* and *Download updates while installing Ubuntu*

![[Pasted image 20231101103951.png]]

Select *Erase disk and install Ubuntu* (this is only for the VM, your computer’s Disk will remain untouched). Select continue on the pop up that appears
1. Choose your time zone and continue
1. Create the computer’s username and password and continue

![[Pasted image 20231101103957.png]]

Wait while everything is installed

![[Pasted image 20231101104003.png]]

- Once the installation is complete, select *Restart Now* on the pop up that appears. Press *Enter* when asked
- You may connect your online accounts or just press *Skip*

![[Pasted image 20231101104009.png]]

- Select *Skip for now* and click *Next*

![[Pasted image 20231101104014.png]]

- If a software updater appears, select *Remind me Later*

![[Pasted image 20231101104020.png]]

1. You can choose to send system info or not, then click *Next*
1. Choose whether or not to use Location Services and then click *Next*



> [!tip] Fullscreen mode
> If you have a single screen, it is easiest to work in the VM without the VirtualBox full-screen mode. To adjust the screen size, right click in the Ubuntu VM and select “Display Settings”. Here you can adjust the screen size. A recommended view of how it can look is the following:

![[Pasted image 20231101103930.png]]
![[Pasted image 20231101103935.png]]
# Tools and Software

You will need software use **ros2**:

- [[#Vscode]]
- [[#Terminator]]
- [[#Pip]]
- [[#Git]]

Before starting to install everything be sure to update and upgrade your system:

```bash
sudo apt update 
sudo apt upgrade
sudo apt update 
sudo apt autoremove
```

## Vscode

- From *Ubuntu Software* select to install Visual Studio Code and open it once finished

![[Pasted image 20231101104030.png]]

Also you can install vscode from the terminal: 

```bash
sudo snap install code --classic
```

- Open VSCode (You may add a shortcut of VSCode to the side bar by right clicking the icon and selecting add to favorites)

Install the following extensions

![[Pasted image 20231101104036.png]]

![[Pasted image 20231101104040.png]]

![[Pasted image 20231101104046.png]]

## Terminator

Terminator is a *terminal multiplexer* enabling to have many terminals opened in a single terminal instance. To install:

```bash
sudo apt install terminator
```

This is a useful app that can have several terminals in a single screen. You can use CTRL+SHIFT+O to split the screen horizontally or CTRL+SHIFT+E to split the screen vertically. For more info go to the following link: <https://www.makeuseof.com/run-multiple-linux-terminals-with-terminator/?newsletter_popup=1>

![[Pasted image 20231101104054.png]]

## Pip

- To install python3 pip enter the command:

```bash
sudo apt install python3-pip
```

## Git

- To install git enter the command:

```bash
sudo apt install git
```

# ROS2

## Installation

- ROS2
   - ROS2 installation (Steps taken from the official guide on <https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html>):
   
> [!tip]
> It is easiest if you open the link of the official guide in FireFox from your Virtual Machine. That way you can copy all the commands shown straight from the page
      

```bash
locale
```

- Enter the following commands (DO NOT SKIP ANY COMMANDS!!):

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg 
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU\_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

sudo apt update
sudo apt install ros-humble-desktop
sudo apt install ros-dev-tools
cd
source /opt/ros/humble/setup.bash && echo "source /opt/ros/humble/setup.bash" >> .bashrc

```

### Python Dependecies

- Python dependencies
- `pip install --user -U empy pyros-genmsg setuptools`

- Install ROS2 build tool - colcon

```bash
sudo apt install python3-colcon-common-extensions
cd
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash && echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> .bashrc
```
