
![img_01][img_01]

> USB Downloader(LN-101)

# Introduction

# How_to_Use

USB Downloader is used to connect the USB port of PC and the 4-pin port of the controller through serial communication.

![img_02][img_02]
![img_03][img_03]

## Serial Communication

- [Download Task Code written in PC using the controller][download_task_code]
- [Print out the result of task code execution on the screen of PC][task_result_print]
- [Virtual robot control of RoboPlus][virtual_robot_control]

## Available Controller
- [CM-100]
- [CM-150]
- [CM-200]
- [CM-700]
- [OpenCM9.04]

**NOTE** : Difference in voltage may cause unstable LN-101 connections. Ensure that both connecting equipment and PC are properly grounded.
{: .notice}

# Check Driver

How to check whether the USB downloader(LN-101) driver is installed correctly.

1. Connect USB Downloader (LN-101) to the USB Port of PC.

    ![img_02][img_02]

2. Select Manage in the popped-up menu shown by right-clicking My Computer.

    ![img_04][img_04]

3. Check USB Serial Converter in Universal Serial Bus Controllers of Device Manager.

    ![img_05][img_05]

4. Check USB Serial Port(COMx) in the list of Ports(COM & LPT). COM Port number may vary depending on each system.

    ![img_06][img_06]

# Install Driver Manually

If you installed RoboPlus, FTDI Driver (USB2Dynamixel, USB Downloader (LN-101) driver) is installed together automatically. If you didn't install the RoboPlus yet, or if the driver is not installed appropriately, please install it manually according to following procedures.
{: .notice}

1. Connect a device to PC. If the driver is not installed yet, Found New Hardware Wizard will be popped up. Install from a list or specific location (Advanced)(S) -> Next(N)

    ![img_07][img_07]

2. Decide the location of Driver. If RoboPlus S/W has been installed automatically, the driver is in LN101 folder of RoboPlus Installation folder. Or if you want to install the newest version, download the newest version VCP driver from [FTDI Driver Download] page.

    ![img_08][img_08]
    
    ![img_09][img_09]

3. Click the Next(N) button to start the installation. Installation of USB Serial Converter driver is completed.

    ![img_10][img_10]

4. Install the USB Serial Port driver in the same way.

    ![img_11][img_11]


# Videos

Setting up the port
<iframe width="560" height="315" src="https://www.youtube.com/embed/UlD4C1XMsgo" frameborder="0" allowfullscreen></iframe>


[FTDI Driver Download]: http://www.ftdichip.com/Drivers/VCP.htm
[img_01]: /images/parts/ln101.jpg
[img_02]: /images/parts/task_download_01.jpg
[img_03]: /images/parts/ln101_to_cm700.png
[img_04]: /images/parts/ln101_01.png
[img_05]: /images/parts/ln101_02.png
[img_06]: /images/parts/ln101_03.png
[img_07]: /images/parts/ln101_04.png
[img_08]: /images/parts/ln101_05.png
[img_09]: /images/parts/ln101_06.png
[img_10]: /images/parts/ln101_07.png
[img_11]: /images/parts/ln101_08.png
