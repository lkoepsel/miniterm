# miniterm as a Python Application

## Introduction
This repository attempts to provide a better solution than *tio*, *PuTTY* or *CoolTerm*. YMMV. Though *CoolTerm* is nice, is cross-platform and provides the ability to connect/reconnect, I have been disappointed with some its possible malware issues. Both *tio* and *PuTTY* lack the ability to easily connect and reconnect from the serial port, making embedded programming a bit laborious.

While my favorite serial application is [**Serial**](https://www.decisivetactics.com/products/serial/) it costs money (**and is well worth it!**) and is macOS only. The former can be a problem for early in career students and those only needing limited serial connectivity. My second best solution is the utility *miniterm* from Python's pyserial library. The only issue is that it requires Python to be installed to use and this doesn't always exist.


## Solutions
The solution is to use *pyinstaller* to create self-standing versions of miniterm. In this repository, there are three versions:
* miniterm_macos_arm64 - Mn (M1 and M2) variants of mac computers
* miniterm_macos_x86 - Intel versions of mac computers
* miniterm_windows10 - Windows version, created in Windows 10, needs testing on Windows 11

## Solution Contents
For each solution above, I created two versions and included the exact file which was used to create the application. A little background, when you use pyinstaller, it can create two versions based on arguments provided:
```bash
# create a one folder version
pyinstaller miniterm.py
# create a one file version
pyinstaller -F miniterm.py 
```

The pyinstaller documentation recommends testing the *_onefolder* version first to ensure the application works well. If so, you can use the *_onefile* version as it is a bit easier to use. In these instructions, I recommend trying the *_onefile* version, first, keep going. If you have issues, attempt to debug with the *_onefolder* version. If you continue to have problems, either stop using this approach or install Python and use the included *miniterm.py* version.
* *miniterm.py* - exact program which was created using pyinstaller
* *miniterm_onefolder* - folder containing the pyinstaller one folder version, use if you have problems with the *_onefile* version
* *miniterm_onefile* - folder containing the pyinstaller one file version

## Installation
* Download the desired one_file solution, as in [for windows](miniterm_windows10/miniterm_onefile/dist), and double-click the downloaded file *miniterm.exe*. If successful it will open a terminal window running miniterm.
* **If not successful**, you can download the [one_folder solution](miniterm_windows10/miniterm_onefolder/dist/miniterm), keep all of the files in a folder and double-click on the *miniterm.exe*, *pyinstaller* comments that the one_folder solution might work, when the one_file solution does not.
* **Finally if all else fails**, install python and run the file [*miniterm.py*](miniterm_windows10/miniterm.py)

## Documentation
See documentation for tools in [pySerial Documentat](https://pyserial.readthedocs.io/en/latest/). The file miniterm.py was downloaded from this [github repo](https://github.com/pyserial/)

One slight change is the baud rate is set automatically to 250000 (that is 250,000 baud).
