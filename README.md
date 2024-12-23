![Oscilloscope IMG](https://github.com/MattSpot10/USB_AutoLaunchSW/blob/main/src/USB_AutoLaunchSW/icon.png)
### **Description**
USB_AutoLaunchSW is a USB event triggered application launcher and optional terminator. This software runs in the background, starts on startup (when installed by the installer), and is accessible through the system tray in Windows. When a USB device insert or remove event is triggered, the software checks the new USB device's Hardware ID against identifiers in the JSON configuration file. If it matches the identifiers in the file, it executes or terminates the software defined in that section of the JSON file.

This software was originally developed to launch the EMBO (EMBedded Oscillsocpe app) when supported STM32 devices were connected, but it has evolved to support all PnP devices and additional configurations.

**Use cases**
- Launching IDEs when a specific USB device is inserted.
- Launching serial monitors when RS-232 FTDI or other serial devices are connected.
- Launching media software when connecting media devices.
- etc.


**Example configuration**
```
{
  "USBSettings": [
    {
      "VendorID": "VID_0483",
      "ProductID": "PID_5740",
      "SerialNumber": "",
      "ExecutablePath": "C:\\Program Files (x86)\\EMBO\\EMBO.exe",
      "StartOnInsert": true,
      "KillOnRemove": true,
      "RunningProcess": ""
    },
    {
      "VendorID": "VID_1234",
      "ProductID": "PID_4321",
      "SerialNumber": "",
      "ExecutablePath": "..path to your exe",
      "StartOnInsert": true,
      "KillOnRemove": true,
      "RunningProcess": ""
    },


...more stuff...


    {
      "VendorID": "VID_6789",
      "ProductID": "PID_9876",
      "SerialNumber": "",
      "ExecutablePath": "..path to your 2nd exe",
      "StartOnInsert": true,
      "KillOnRemove": true,
      "RunningProcess": ""
    }
  ]
}
```

**Notes:**
- The ```"RunningProcess": ""``` property doesn't do anything, so it can be left blank but included for additional configurations.
- All PnP (Plug and Play) devices should work.
- The config.JSON file can be accessed through the ```Configure``` option in the system tray, after which the user will need to select the ```Reset``` option to reload the configuration.

**Additional info**
- This software was developed in Visual Studio, and the installer was made with HM NIS EDIT.

### **Download Installer (Windows)**
[USB_AutoLaunchSW-1.0.1_Win32_installer.zip](https://github.com/MattSpot10/USB_AutoLaunchSW/releases/download/v1.0.1/USB_AutoLaunchSW-1.0.1_Win32_Installer.exe)

(If the app does not seem to work after install, try running it as administrator.)
