---
layout: Project3
---

# 1.Introduction

Arduino IDE is [OpenCR] and [OpenCM9.04] compatible development tool.  
[OpenCM IDE] can be replaced with Arduino IDE, and it is recommended to use Arduino IDE if possible.  
Arduino IDE allows users to apply [Dynamixel SDK] and [Dynamixel Workbench] when writing sketches.  

# 2.Software_Installation

- `Download` [Arduino IDE]

**Install on Linux**

**USB Port Settings**

#### For OpenCR
Make the OpenCR USB port be able to upload the Arduino IDE program without root permission.

```bash
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
$ sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
$ sudo udevadm control --reload-rules
$ sudo udevadm trigger
```

![](/images/sw/7_1_1_usb_port_setting.png)

#### For OpenCM9.04
Make the OpenCM9.04 USB port be able to upload the Arduino IDE program without root permission.
```
wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCM9.04/master/99-opencm-cdc.rules
sudo cp ./99-opencm-cdc.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
sudo udevadm trigger
```

**Compiler Settings**
Since the OpenCR and OpenCM9.04 libraries are built for 32 bit platform, 64 bit PC needs the 32 bit compiler relevants for the ArduinoIDE.

```bash
$ sudo apt-get install libncurses5-dev:i386
```

![](/images/sw/7_1_2_compiler_settings.png)

**Install Arduino IDE(Linux)**
Download the latest version of Arduino IDE from the official arduino homepage, and install it. Currently, OpenCR and OpenCM9.04 will be compatible with the version 1.6.4 or later.

[https://www.arduino.cc/en/Main/Software](https://www.arduino.cc/en/Main/Software)

Then, extract the downloaded file to the desired folder and execute the installation file from the terminal. In this case, the example shown below makes the folder tools in the user’s top folder (~/). This folder will act as the Arduino IDE folder.

```bash
$ cd ~/tools/arduino-1.8.3
$ ./install.sh
```

Set the file path of installed Arduino IDE as an absolute path named PATH in the bashrc file. Here recommends to use gedit editor. (Use another editor, if necessary.) Finally, source it to apply the changes.

```bash
$ gedit ~/.bashrc
$ export PATH=$PATH:$HOME/tools/arduino-1.8.3
$ source ~/.bashrc
```

**Run Arduino IDE(Linux)**
To run the Arduino IDE on Linux platform, type into the terminal as follows.

```bash
$ arduino
```

![](/images/sw/ide0.png)

**Porting to Arduino IDE(Linux)**


#### Preferences
After Arduino IDE is run, click File → Preferences in the top menu of the IDE. When the Preferences window appears, copy and paste following link to the Additional Boards Manager URLs textbox.  
Please select the appropriate file URL based on your board.

##### For OpenCR

```
https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json
```

![](/images/sw/ide1.png)

##### For OpenCM9.04

```
https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCM9.04/master/arduino/opencm_release/package_opencm9.04_index.json
```

![](/images/sw/opencm9.04_linux_1.png)

#### Install the board package via Boards Manager
Click Tools → Board → Boards Manager. This step may take more than 20 minutes depending on the network status.

![](/assets/images/platform/turtlebot3/preparation/ide2.png)

##### For OpenCR

Type OpenCR into the textbox to find the OpenCR by ROBOTIS package. After it finds out, click Install.

![](/images/sw/ide3.png)

After the installation, “INSTALLED” will be appeared.

![](/images/sw/ide4.png)

See if OpenCR Board is now on the list of Tools → Board. Click this to import the OpenCR Board source.

![](/images/sw/ide5.png)

##### For OpenCM9.04

Type OpenCM9.04 into the textbox to find the OpenCM9.04 by ROBOTIS package. After it finds out, click Install.

![](/images/sw/opencm9.04_linux_3.png)

After the installation, “INSTALLED” will be appeared.

![](/images/sw/opencm9.04_linux_4.png)

See if OpenCM9.04 Board is now on the list of Tools → Board. Click this to import the OpenCM9.04 Board source.

![](/images/sw/opencm9.04_linux_5.png)

#### Port Setting
This step shows the port setting for the program uploads. The OpenCR/OpenCM9.04 should be connected to the PC via micro USB port.

Select Tools → Port → /dev/ttyACM0.

**WARNING** : The last digit value **0** in the string **/dev/ttyACM0** might be different depend on the USB connection environment.
{: .notice--warning}

![](/images/sw/ide6.png)

**Remove Modemmanager**

Only **OpenCR** requires this process. If you are using OpenCM9.04, please skip this section.
{: .notice--warning}

After programming with the Arduino IDE and uploading the program to the OpenCR, the OpenCR will be restarted and be reconnected.  
At the same moment, the modem-related packages of the Linux will send the AT command to manage the device.  
Thus indicates an connection error on the OpenCR, so this step should be done previously.

```bash
$ sudo apt-get purge modemmanager
```


**Install on Mac**

**Install Arduino IDE(Mac)**

Download the latest version of Arduino IDE from the official arduino homepage, and install it. Currently, OpenCR and OpenCM9.04 will be compatible with the version 1.6.4 or later.

- `Download` [Arduino IDE]

**Run Arduino IDE(Mac)

To run the Arduino IDE on Mac platform, click the Arduino IDE icon as follows.

![](/images/sw/arduino_mac_01.png)

![](/images/sw/arduino_mac_02.png)

**Porting to Arduino IDE(Mac)**

#### Preferences
After Arduino IDE is run, click File → Preferences in the top menu of the IDE.  
When the Preferences window appears, copy and paste following link to the Additional Boards Manager URLs textbox.  
Please select the appropriate file URL based on your board.

##### For OpenCR

```
https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json
```

![](/images/sw/arduino_mac_03.png)

##### For OpenCM9.04

```
https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCM9.04/master/arduino/opencm_release/package_opencm9.04_index.json
```

![](/images/sw/opencm9.04_mac_1.png)

#### Install the board package via Boards Manager
Click Tools → Board → Boards Manager. This step may take more than 20 minutes depending on the network status.

![](/images/sw/arduino_mac_04.png)

##### For OpenCR

Type OpenCR into the textbox to find the OpenCR by ROBOTIS package. Install of the OpenCR package.  
After the installation, “INSTALLED” will be appeared.

See if OpenCR Board is now on the list of Tools → Board. Click this to import the OpenCR Board source.

![](/images/sw/arduino_mac_05.png)

##### For OpenCM9.04

Type OpenCM9.04 into the textbox to find the OpenCM9.04 by ROBOTIS package. After it finds out, click Install.

![](/images/sw/opencm9.04_mac_3.png)

After the installation, “INSTALLED” will be appeared.

![](/images/sw/opencm9.04_mac_4.png)

See if OpenCM9.04 Board is now on the list of Tools → Board. Click this to import the OpenCM9.04 Board source.

#### Port setting
This step shows the port setting for the program uploads. The OpenCR/OpenCM9.04 should be connected to the PC via micro USB port.  
Select Tools → Port → /dev/cu.usbmodem1411

**CAUTION** : The value of **/dev/cu.usbmodem1411** may be different depending on the environment connected to the PC.
{: .notice--warning}

![](/images/sw//arduino_mac_06.png)

**Install on Windows**

**Install Driver**
To use OpenCR and OpenCM9.04 micro USB port as a serial port in Windows, you need a USB CDC driver. You can install the USB driver provided by ST.

[http://www.st.com/en/development-tools/stsw-stm32102.html](http://www.st.com/en/development-tools/stsw-stm32102.html)

**Install Arduino IDE(Windows)**
Download the latest version of Arduino IDE from the official arduino homepage, and install it. Currently, OpenCR and OpenCM9.04 will be compatible with the version 1.6.4 or later.

- `Download` [Arduino IDE]

The Arduino IDE for Windows is available as an installation version and a compressed version, so you can install it using your preferred method.

**Porting to Arduino IDE(Windows)**

#### Preferences
After Arduino IDE is run, click File → Preferences in the top menu of the IDE.  
When the Preferences window appears, copy and paste following link to the Additional Boards Manager URLs textbox.  
Please select the appropriate file URL based on your board.

##### For OpenCR

```
https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json
```

#### Install the OpenCR package via Boards Manager
This step may take more than 20 minutes depending on the network status.

##### For OpenCR

Click Tools → Board → Boards Manager.

![](/images/sw/opencm904_win_2.png)

Type OpenCR into the textbox to find the OpenCR by ROBOTIS package. After it finds out, click Install.

![](/images/sw/arduino_win_01.png)

After the installation, “INSTALLED” will be appeared.

![](/images/sw/arduino_win_02.png)

See if OpenCR Board is now on the list of Tools → Board. Click this to import the OpenCR Board source.


##### For OpenCM9.04

Type OpenCM9.04 into the textbox to find the OpenCM9.04 by ROBOTIS package. After it finds out, click Install.

![](/images/sw/opencm904_win_3.png)

After the installation, “INSTALLED” will be appeared.

![](/images/sw/opencm904_win_4.png)

See if OpenCM9.04 Board is now on the list of Tools → Board. Click this to import the OpenCM9.04 Board source.

![](/images/sw/opencm904_win_5.png)

#### Port setting
This step shows the port setting for the program uploads. The OpenCR/OpenCM9.04 should be connected to the PC via micro USB port.  
Select Tools → Port → COM1.

**CAUTION** : The value of **COM1** may be different depending on the environment connected to the PC.
{: .notice--warning}


# 3.Examples

**OpenCM9.04 Examples**

1. [LED]{: .popup}
2. [Button]{: .popup}
3. [Buzzer]{: .popup}
4. [PWM]{: .popup}
5. [EEPROM]{: .popup}
6. [DynamixelWorkbench]{: .popup}
7. [Servo]{: .popup}
8. [SD Card]{: .popup}
9. [MS5540S]{: .popup}
10. [MPU6050 DMP]{: .popup}
11. [0.96" OLED LCD]{: .popup}

# 4.Advanced Users

**Writing Bootloader(OpenCR)**

**CAUTION** : Perform Bootloader update only when the OpenCR bootloader has been updated. The product already has the default bootloader.
{: .notice--warning}

The STM32F7xx, which is used for the main MCU on the OpenCR board, supports DFU(Device Firmware Upgrade). This enables the built-in bootloader of the MCU by itself to boot the DFU protocol by using USB, primarily for the bootloader initialization, the recovery mode, and the bootloader update. The biggest advantage to let the users be able to use bootloader with USB but no other JTAG equipment. Write the firmware by using the DFU mode which is embedded in MCU without writing / debugging equipment, such as STLink.

#### Programmer Setting
Select Tools → DFU-UTIL

![](/images/sw/bootloader_19.png)

#### Run DFU mode.
Press the `Reset Button` while the `Boot Button` is being pushed. This activates the DFU mode.  

#### For Linux
If you successfully entered to DFU mode, you will be able to find `STMicroelectronics STM Device in DFU Mode` text string when *lsusb* is entered in the terminal.

![](/images/sw/ide10.png)

#### For Windows

If you successfully entered to DFU mode, you will be able to find `STM32 BOOTLOADER` under the **Universal Serial Bus devices** in Device Manager.

![](/images/sw/dfu_mode_win.png)

#### Download the bootloader.

Click Tools → Burn Bootloader to download the bootloader.

![](/images/sw/ide9.png)
