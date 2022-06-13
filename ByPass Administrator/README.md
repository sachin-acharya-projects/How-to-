# ByPass UAC Elevation in Windows
__________________
**Create a shortcut file with any name and target it to**
````
C:\Windows\System32\cmd.exe /min /C "set __COMPAT_LAYER=RUNASINVOKER && start "" "[path-to-your-program]""
````

**and you can simply run it as usaul.**

_(Note: If a program required UAC elevation, it won't work well with this method. Eg. If a program create a folder in some forbidden location and need UAC elevation, this method will that program to fail due to lack of UAC)_
