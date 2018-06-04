
# 1.Introduction

The `ROBOTIS OpenCM` is a development Software and download tool for the OpenCM9.04 embedded board.  
Sources of the ROBOTIS OpenCM are released under licenses of their respective authors.  
Copyright (c)  ROBOTIS Co., Ltd. Modified or newly-created codes are released under the GNUGPL or LGPL licenses.  
For more information on the OpenCM9.04 refer to the Appendix section of the e-manuals.  

- [GNU GPL](http://opensource.org/licenses/gpl-license.php)
- [GNL LGPL](http://opensource.org/licenses/lgpl-license.php)

# 2.ROBOTIS OpenCM Software Download

OpenCM9.04 uses the ROBOTIS OpenCM Integrated Developmental Environment (IDE) to allow users to program with ease.  
The download link for the ROBOTIS OpenCM IDE can be found below:

- [Windows XP, Vista, 7, 8] 32bit/64bit : [Download](http://www.robotis.com/service/download.php?no=47)
- [Mac OS X] Tested in OS X 10.12.2 : [Download](http://www.robotis.com/service/download.php?no=48)
- [Linux 64bit] Tested in Ubuntu 12.04 : [Download](http://www.robotis.com/service/download.php?no=49)
- [Linux 32bit] Tested in Ubuntu 10.10 : [Dowload](http://www.robotis.com/service/download.php?no=50)


# 3.Getting_Started

**Install_Software**

**Windows**

**Prepare the OpenCM9.04 and USB cable**

For the cable you must prepare an Android phone/pad Micro-B type USB cable. (This is included as a component of the package for the B type, and for the A type you must purchase through an accessory kit. Android smartphone cable is supported.)

![](/images/sw/opencm_ide_001.png)

> Micro-B USB cable : same as Android smartphone

**Download the Windows release for ROBOTIS OpenCM IDE**

Download the latest version from the ROBOTIS E-manual(support.robotis.com) site and unzip the file in an adequate directory, which will contain the execution file ROBOTIS_OpenCM.exe and the USB driver folder(\drivers) as shown below.

![](/images/sw/opencm_ide_002.png)

> Directory structure after unzipping the file

Note that the ROBOTIS OpenCM is a portable program that only needs to be unzipped and executed without the need for any separate installation process. If you wish to remove the program, you simply need to delete the directly fully.

**Connect the OpenCM9.04 to the PC**

For the installation of the USB driver, simply connect the OpenCM9.04 to the PC using the USB cable as shown below.

![](/images/sw/opencm_ide_003.png)

> Figure 2.4.1-4 Connecting the OpenCM9.04 to the PC

However we do recommend you avoid connecting to a USB hub that is in use with many other USB devices, and instead you connect to the PC directly. There can be rare cases in which if there is not enough electric current from the USB hub then the download can fail.

**Driver Installation**

For Window 8 or 10, go to "PC settings -> Update and recovery -> Recovery -> Advanced startup -> Troubleshoot -> Advanced options -> Startup Settings -> Restart -> Select 7) Disable driver signature enforcement, and then restart" and then install using Run as administrator.  
In the previous step, connecting the OpenCM board to the PC will make a device called “ROBOTIS Virtual COM Port” appear in the Device Manager.

![](/images/sw/opencm_ide_004.png)

Right-click on that device and select “Update Driver Software”.

![](/images/sw/opencm_ide_005.png)

Next select “Browse my computer for driver software”.

![](/images/sw/opencm_ide_006.png)

Click on “Browse” and select the directory that you unzipped above(ROBOTIS\drivers).

![](/images/sw/opencm_ide_007.png)

Click Next and the installation proceeds.  
If the USB driver is installed successfully, a message will appear that says “Windows has successfully updated your driver software” as shown below.

![](/images/sw/opencm_ide_008.png)

At this stage it is important to check in the Device Manager what COM Port number the ROBOTIS Virtual COM Port has just been installed as.  
Connecting to another USB port may change the COM Port number so if you connected to another port then check again and proceed to download.

![](/images/sw/opencm_ide_009.png)

#### Run ROBOTIS_OpenCM.exe

In the unzipped directory(\ROBOTIS) double-click on the file ROBOTIS_OpenCM.exe.

![](/images/sw/opencm_ide_010.png)

This will execute the ROBOTIS OpenCM tool as shown below.

![](/images/sw/opencm_ide_011.png)

##### Open the Example Blink

Go to File → Examples → 01.Basics → b_Blink

![](/images/sw/opencm_ide_012.png)

##### Select the Board

In Tools → Board, select ROBOTIS OpenCM9.04.

![](/images/sw/opencm_ide_013.png)

##### Select the Serial Port

Make sure you select the COM Port number that you checked in the previous step.

![](/images/sw/opencm_ide_014.png)

##### Proceed to Download

Click on the Download button as shown below. As the download begins the board’s green LED is continuously turned on. Once the download is complete the board resets and the Blink example is executed, and the LED blinks.

![](/images/sw/opencm_ide_015.png)

**NOTE** : If the power turns on for the board and the green LED is continuously turned on then restart the Download. Please refer to the Emergency Recovery Mode(Force Download) section.
{: .notice}

### [MAC OS X](#mac-os-x)

#### Download the Mac OS X release for ROBOTIS OpenCM

Download the installation image file(dmg) for Mac OS X from the E-manual.

![](/images/sw/opencm_ide_016.png)

When the download finishes, double-click on the dmg file below and proceed to Mount.

![](/images/sw/opencm_ide_017.png)

After mounting, when an installation window appears, click on the Robotis icon with the mouse and drag it to Application.

![](/images/sw/opencm_ide_018.png)

Then the installation will proceed as below.

![](/images/sw/opencm_ide_019.png)

#### Run the ROBOTIS OpenCM

Using Finder, look in the Application folder to find the ROBOTIS.app application package and double-click on it to run the program.

![](/images/sw/opencm_ide_020.png)

As in the figure below, select the Open button.

![](/images/sw/opencm_ide_021.png)

The ROBOTIS OpenCM is executed as shown below.

![](/images/sw/opencm_ide_022.png)

#### Open the Example Blink

Go to File → Examples → 01. Basics → b_Blink

![](/images/sw/opencm_ide_023.png)

#### Select Board

Select ROBOTIS OpenCM9.04.

![](/images/sw/opencm_ide_024.png)

#### Select Serial Port.

Select tty.usbmodemXXX. The number on the end is different for each PC.

![](/images/sw/opencm_ide_025.png)

#### Proceed to Download

Click on the Download button as shown below. As the download begins the board’s green LED is continuously turned on. Once the download is complete the board resets and the Blink example is executed, and the LED blinks.

![](/images/sw/opencm_ide_026.png)

**NOTE** : If the board’s green Status LED does not turn on even after clicking on the Download button, press on the User button and while keeping the button pressed connect the USB to the PC.
{: .notice}

**NOTE** : If the power turns on for the board and the green LED is continuously turned on then restart the Download. Please refer to the Emergency Recovery Mode(Force Download) section.
{: .notice}
