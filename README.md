# miniterm as a Python Application

## Introduction
This repository attempts to provide a better solution than *tio*, *PuTTY* or *CoolTerm*. YMMV. Though *CoolTerm* is nice, is cross-platform and provides the ability to connect/reconnect, I have been disappointed with some its possible malware issues. Both *tio* and *PuTTY* lack the ability to easily connect and reconnect from the serial port, making embedded programming a bit laborious.

While my favorite serial application is [**Serial**](https://www.decisivetactics.com/products/serial/) it costs money (**and is well worth it!**) and is macOS only. The former can be a problem for early in career students and those only needing limited serial connectivity. My second best solution is the utility *miniterm* from Python's pyserial library. The only issue is that it requires Python to be installed to use and this doesn't always exist.

## Why Miniterm
Why is miniterm a good solution? It allows you to easily connect and disconnect without exiting the application. From the [documentation](https://pyserial.readthedocs.io/en/latest/tools.html#miniterm):

*"Ctrl+T z suspends the connection (port is opened) and reconnects when a key is pressed. This can be used to temporarily access the serial port with an other application, without exiting miniterm. If reconnecting fails it is also possible to exit (Ctrl+]) or change the port (p)."*

Which means you can have two terminal windows open, one to use for `make flash` and the other is running miniterm, where you *Ctrl+T z* and a keystroke to disconnect/connect, respectively.


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

At this poiont in time, the easiest method to download the solutions is to clone the repository. Use `git clone` to create the repository on your system. You can delete the two un-needed solutions, Windows and macos_ARM64, for example if you have an Intel Mac.

* To test the desired one_file solution, *as in windows*, go to *miniterm_windows10/miniterm_onefile/dist*, and double-click the downloaded file *miniterm.exe*. If successful it will open a terminal window running miniterm.
* **If not successful**, you can test the *one_folder Windows solution*, go to *miniterm_windows10/miniterm_onefolder/dist*, go into the folder and double-click on the *miniterm.exe* file. Once again, it should open a terminal. *The solution creater (pyinstaller) comments that the one_folder solution might work, when the one_file solution does not.*
* **Finally if all else fails**, install python and run the file [*miniterm.py*](miniterm_windows10/miniterm.py). While this doesn't solve the initial problem, it helps you solve why this solution isn't working **AND** provides the ability to disconnect and reconnect *miniterm* without exiting the application.

The instructions are the same for *macOS*, simply point to the desired versions:
* **macOS x86 onefile** - *miniterm_macos_x86/miniterm_onefile/dist*
* **macOS x86 onefolder** - *miniterm_macos_x86/miniterm_onefolder/dist*
* **macOS x86 miniterm.py** - *miniterm_macos_x86/miniterm.py*


* **macOS arm64 onefile** - *miniterm_macos_arm64/miniterm_onefile/dist*
* **macOS arm64 onefolder** - *miniterm_macos_arm64/miniterm_onefolder/dist*
* **macOS arm64 miniterm.py** - *miniterm_macos_arm64/miniterm.py*

## Documentation
See documentation for tools in [pySerial Documentation](https://pyserial.readthedocs.io/en/latest/). The file miniterm.py was downloaded from this [github repo](https://github.com/pyserial/).

**One change is the baud rate is set automatically to 250000 (that is 250,000 baud).**
