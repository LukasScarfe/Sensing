Keithley Instruments
Release Note for 24XX-851C05
Ke24xx VXIPnP Driver for the Keithley Model 2400 Series SourceMeters
5/26/2016

IMPORTANT: To work properly with the driver, your instrument must have a compatible version of firmware.  Refer to section 3 (System Requirements) below for specific details regarding the required firmware version for your instrument.  

Visit www.tek.com/keithley for upgrade instructions if your instrument's firmware is not a compatible version.  The instrument's firmware version is shown on the display when the instrument is first powered up, immediately to the right of the model number.

This document provides additional information for the installation and use of the Ke24xx VXIPnP Driver for LabVIEW and LabWindows CVI, Visual Basic, and C/C++.


Table of Contents
----------------------------------------------
1	Introduction
2	New Features
      2.1	Release 3.2 (24XX-851C05)
      2.2	Release 3.1 (24XX-851C04)
      2.3	Release 3.00 (24XX-851C03)
      2.4	Release 2.50 (24XX-851CV2.04)
      2.5	Release 2.04 (24XX-851CV2.04)
      2.6	Release 2.03 (24XX-851CV2.03)
      2.7	Release 2.01 (24XX-851CV2.01)
3	System Requirements
      3.1	Supported Operating Systems and System Software
4	Installation
      4.1	GPIB Controller Installation
      4.2	Connecting your Computer to your Instrument
      4.3	Upgrading from a previous version of the Instrument Driver
      4.4	Instrument Driver Installation
      4.4.1	Installing the driver from the Web
5	Using the Instrument Driver
      5.1.1	Error Codes
5.2	VISA resources
      5.2.1	GPIB
      5.2.2	Example of using VISA resources:
5.3	Using the Example Programs
      5.3.1	Visual BASIC User
      5.3.2	LabVIEW User
5.4	Using the driver with LabVIEW
6	Known problems and issues
      6.1	Missing Functionality/Functionality Not Supported
      6.2	Assumptions made in the Model 24xx VXIPnP Driver
      6.3	Ke24xx_Spoll and RS232
7	Copyright Notice



----------------------------------------------
1 Introduction

The components described below are provided as part of the Ke24xx VXIPnP Driver for the Model 2400 instruments.  Some shortcuts for them are added to the Keithley Instruments folder on your Start Menu.

----------------------------------------------
2 New Features

2.1 Included in this release-Version 3.2 (24XX-851C05)
Fixed issue where upgrading from previous versions was deleting the ke24xx_32.dll file.

2.2 Included in this release-Version 3.1 (24XX-851C04)
Updated to support for Microsoft Windows 10.

2.3 Included in this release-Version 3.00 (24XX-851C03)
Fixed issue to not over-write newer CVI files.

2.4 Release 2.50 (24XX-851CV2.04)
Added support for new 2401 instrument.

Now supports the following instruments:
2400, 2401, 2410, 2420, 2425, 2430, 2440
2400-C, 2410-C, 2420-C, 2425-C, 2430-C, 2440-C, 2400-OSRAM

2.5 Release 2.04 (24XX-851CV2.04)
Changed a parameter size in the linked list that may or may not be causing a crash when calling Ke24xx_init. Seems to be an issue with newer versions of LabWindows/CVI

2.6 Release 2.03 (24XX-851CV2.03)
This release fixes an issue in Agilent VISA. The Ke24xx_init function would generate an error Hex bfff001e,"VI_ERROR_NSUP_ATTR_STATE: Bad
Attribute state specified"

The previous installer only checked for NI VISA and if it wasn't detected then it would abort. This release checks for any VISA and if present it will install correctly. If VISA is not found then it will warn the customer and abort.

2.7 Release 2.01 (24XX-851CV2.01)
Version 2.01 is that same as version 2.0 except that this installer does not install NI-VISA any more. NI-VISA 2.5 or greater must be on the machine for this driver to install.

Now supports the following instruments:
2400, 2410, 2420, 2425, 2430, 2440
2400-C, 2410-C, 2420-C, 2425-C, 2430-C, 2440-C
2400-OSRAM



The driver uses VISA to communicate with your instrument. This software driver supports many Application Development Environments under Windows, such as Visual Basic, C/C++, LabVIEW, LabWindows/CVI. Examples and an on-line help utility are provided to help programmers build their custom applications.



----------------------------------------------
3 System Requirements

Pentium-class PC.

2400 firmware release C22 or later. For the 2400-OSRAM you will need release C25 or later.

VISA:
    The following implementations of VISA are compliant with this driver: NI-VISA™, TekVISA™, AGILENT IO Libraries Suite™.

    The Keithley I/O Layer supplies a NI-VISA™ runtime. Downloads are available at www.tek.com/keithley or you may follow the link below:
http://www.tek.com/search/apachesolr_search/%22Keithley%20I/O%20Layer%22?filters=type%3A%28%22software%22%29

Supported communication buses are GPIB and RS232.

NOTE: It is strongly recommended that your computer and instrument be powered by an Uninterruptible Power Supply (UPS) when running a critical application. 

3.1 Supported Operating Systems and System Software

Windows 10 Pro & Enterprise (32-bit & 64-bit)
Windows 8 Pro & Enterprise (32-bit & 64-bit)
Windows 7 Professional (32-bit & 64-bit) service pack 1 or later 
Windows Vista Business & Enterprise & Ultimate (32-bit & 64-bit) service pack 2 or later
Windows XP Professional service pack 3 or later (32-bit only)
Windows 2000 Service Pack 4 or later

----------------------------------------------
4 Installation
   
4.1 GPIB Controller Installation

If you will be using GPIB to communicate with your instrument, you must have a compatible GPIB controller card and associated software driver installed in your computer before installing the Instrument Driver.

The driver is compatible with the following GPIB controller cards:

Keithley Instruments PCI GPIB cards
 - KPCI-488A with driver version 8.3 or higher
 - KPCI-488LPA with driver version 3.12.1 or higher

Keithley Instruments USB-to-GPIB adaptors
- KUSB-488A with driver version 8.3 or higher
- KUSB-488B with driver version 3.12.1 or higher (install as NI Command Compatible)

NI VISA compatible GPIB controllers


4.2 Connecting your Computer to your Instrument

Connect your instrument to your computer using a standard GPIB interface cable or using a DB9 to DB9 straight through cable (not Null modem) for RS232 communication.

For GPIB communication you just need to set the instrument to a unique GPIB address so it doesn't clash with any other instrument connected to the same bus.

For RS232 communication the Keithley Model 2400 Series SourceMeters Instruments default to a carriage return (CR) for the terminating character. You should change this to line feed (LF) on the instrument. The driver also defaults to 9600baud and with flow-control set to Xon/Xoff. If you want to change this then call the VISA attributes that set these parameters with the handle you get back from the Ke24xx_init function.

4.3 Upgrading from a previous version of the Instrument Driver

If you have an earlier version of the driver software installed on your computer, uninstall it by following the steps below before installing this version.

First of all backup the file visaconf.ini, which is located in the VXIPnP\Win95\NiVisa directory or the VXIPnP\WinNT\NiVisa directory. The path varies depending on what operating system you are running.

Using the Add/Remove Programs applet in the Control Panel, uninstall the following   components:

Keithley 24XX SourceMeter Driver Or Keithley 24XX Driver

Reboot your computer.

When you install the new driver put the backed up copy of the visaconf.ini back in its original location.

4.4 Instrument Driver Installation
4.4.1 Installing the driver from the Web

If you have a previous version of the Instrument Driver installed on your computer, uninstall it as described above before installing the new version.

Download the driver software from the Keithley Web site, www.tek.com/keithley or you may search using the following link:
http://www.tek.com/search/apachesolr_search/24xx?filters=type%3A%28%22software%22%29

The software should be downloaded to a temporary directory.

Run the downloaded file from the temporary directory.

Follow the instructions on the screen to install the software.  Note: during the early part of the installation, the installation utility may appear to stop for a minute or so.  This is normal and the utility will continue running in a short while.

When the installation is complete, reboot your computer.

----------------------------------------------
5 Using the Instrument Driver

To connect to the instrument via the driver you need to first call Ke24xx_init. The first parameter for either function is a VISA resource string, which indicates to the I/O layer which communication device you want to use to connect to the instrument and in most cases the address of the instrument.  This can be specified using a VISA Resource string.  

5.1.1 Error Codes

Error codes are returned as the return value of each instrument driver function. A program should examine this value after each call to an instrument driver function to determine if any error occurred. Possible error codes and their meanings are listed with the corresponding instrument driver function in the Windows help file.

5.2 VISA resources
5.2.1 GPIB

For GPIB instruments, you would use a resource string of the following format:

"GPIBx::yy::INSTR".
x is the GPIB card number.
yy is the GPIB address of the instrument.

5.2.2 Example of using VISA resources:

Ke24xx_init("GPIB0::24::INSTR ",
VI_TRUE,
VI_TRUE,
handle)
would connect to a 2400 on GPIB address 24.

Ke24xx_init("ASRL1::INSTR ",
VI_TRUE,
VI_TRUE,
handle)
would connect to a 2400 on COM Port1

5.3 Using the Example Programs

The Ke24xx Driver includes an example program written in Visual Basic.  The example demonstrates how to perform a Source Current and Measure Voltage linear sweep, using the driver. The example program is hard coded to use a 24xx at GPIB address 24 using a Keithley or CEC GPIB interface card for communications.  If you are using a different bus, address, or interface card, you must edit the example program to change the address, bus, or interface.

5.3.1 Visual BASIC User

There is no Ke24xx.bas file for the Visual BASIC user. The preferred way to access the Dll is to go to the References menu selection under the Project menu. Use the "Browse" button and select the Ke24xx_32.dll, which is in the VXIPnP bin directory.  Refer to the online help or use the "Object Browser", under the View menu to view the Ke24xx_32 library, to get a list of the function calls and defined constants.

5.3.2 LabVIEW User

Just a reminder that any VI that has an output parameter requires that you assign a control (UINT32) to the size of the parameter otherwise it will crash. If it is outputting a single value then the size should be 1 where as if it is and array of data then you will need the correct size of the array.

5.4 Using the driver with LabVIEW 

If LabVIEW is already installed on your computer when the driver is installed, the LabVIEW VIs will be installed in the proper subdirectory of the LabVIEW directory so that they are directly accessible from within LabVIEW.

If LabVIEW is not installed on your computer when the driver is installed, the LabVIEW VIs will placed in a subdirectory of the Keithley Instruments directory.  Once LabVIEW has been installed, the VIs must be copied to the proper subdirectory under LabVIEW before they can be used.  This directory is typically:

C:\Program Files\National Instruments\ LabVIEW X\inst.lib\Ke24xx

Depending on the particular driver, there may be separate versions of the VIs for LabVIEW 5.x and 6.x, in which case they will be installed into separate directories.  Copy the appropriate version of the VIs into the National Instrument directory tree.

----------------------------------------------
6 Known problems and issues

6.1 Missing Functionality/Functionality Not Supported

The following is a list of functionality that is in the Keithley Model 2400 Series SourceMeters Instruments but not supported by the 24xxVXIPnP driver. As a workaround, the user can use the Ke24xx_WriteInstrData and Ke24xx_ReadInstrData functions to send and receive commands/data to the instrument.

Functionality Not Supported in the Ke24xx VXIPnP driver:
* User defined Math expressions
* Relative
* Limits (1 thru 12)
* Binning
* Math (mean, sdev, max, min, pkpk)
* NPLC caching

6.2 Assumptions made in the Model 24xx VXIPnP Driver 
* All read functions transfer the data from the instrument in binary mode for GPIB communications and ASCII mode for RS232 communications.

* These high level functions are very specific and have numerous parameters.
Ke24xx_Configure_DC_IV 
Ke24xx_Perform_DC_IV
Ke24xx_ Configure _DC_VI
Ke24xx_Perform_DC_VI
Ke24xx_Configure_Sweep_IV
Ke24xx_Perform_Sweep_IV
Ke24xx_Configure_Sweep_VI
Ke24xx_Perform_Sweep_VI 
Ke24xx_Configure_List_IV
Ke24xx_Perform_List_IV
Ke24xx_Configure_List_VI
Ke24xx_Perform_List_VI
The Sweep and List functions return both voltage and current so the array you pass in for the returned data should be twice as long as the number of points or samples taken. The DC functions return just a single element. If it's sourcing current then it returns voltage and if sourcing voltage then it return current.

* The perform functions above all call the Configure function counterpart. 

6.3 Ke24xx_Spoll and RS232
If you enable bits in the *SRE register to generate a SRQ then on RS232 it doesn't work correctly due to a firmware bug. All versions of the 2400 firmware up to C25 have this bug. The VB example, Model2400ex1, shows this problem. If you use it to connect to a 2400 on RS232 then you can run the sweep once but when you run it twice a timeout error is generated. There is no known work a round at present. Check the Keithley Web site to see if we have a FAQ on a work around or have fixed the firmware.  - PR22327


----------------------------------------------
7 Copyright Notice

The Ke24xx VXIPnP Instrument Driver is Copyright (c) Keithley Instruments 2007-2016. All Rights Reserved.

----------------------------------------------
End of Release notes.
----------------------------------------------

