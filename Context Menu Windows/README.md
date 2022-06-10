# ADDING CONTEXT MENU IN WINDOWS
_________________
> Redirects  
> [Normal Context Menu](#normal-context-menu)  
> [Cascading Context Menu](#cascading-context-menu)  
> [File Context Menu](#file-context-menu)  
________________________________________________________
## Foremost thing to do
Type ````regedit```` in RUN or Start Menu Search box and press Enter. It’ll open Registry Editor.  
## Normal Context Menu
1. [Run Registry Editor](#foremost-thing-to-do)
2. Now go to following key:  
    * Context menu for right click on folders in left panel of Windows Explorer or on background of a directory in right panel: 
        * if you are Administrator  
        ````
            HKEY_CLASSES_ROOT\Directory\Background\shell
        ````
        * if you are Normal User  
        ````
            HKEY_CURRENT_USER\Software\Classes\directory\Background\shell
        ````
    * Context menu for right click on folders in right panel of Windows Explorer:
        * if you are an Administrator  
        ````
            HKEY_CLASSES_ROOT\Directory\shell
        ````
        * if you are Normal User  
        ````
            HKEY_CURRENT_USER\Software\Classes\directory\shell
        ````
## Cacading Context Menu
[Reference](https://www.askvg.com/add-cascading-menus-for-your-favorite-programs-in-windows-7-desktop-context-menu/)  

__Steps__
1. [Run Registry Editor](#foremost-thing-to-do)
2. Now go to following key:  

    * For Desktop Context Menu  
        ````
        HKEY_CLASSES_ROOT\DesktopBackground\Shell
        ````
  
    * For My Computer(This PC) Context Menu  
        ````
        HKEY_CLASSES_ROOT\CLSID\{20D04FE0-3AEA-1069-A2D8-08002B30309D}\shell
        ````

3. Now we’ll need to create a new key under __Shell__ key. Right-click on __Shell__ key and select __New -> Key__. Give the new key any desired name e.g. __Menu_1__  

4. Now select this newly created key __Menu_1__ and in right-side pane, we’ll need to create following 4 String values:
    * `MUIVerb`
    * `SubCommands`
    * `Icon`
    * `Position`  

    __Icon__ and __Position__ are optional but __MUIVerb__ and __SubCommands__ are compulsory.

    __MUIVerb__ contains the name of cascading menu which will be displayed in the context menu. You can set its value to any desired name like Apps, Browsers, etc. Feel free to set any name.

    __SubCommands__ contains list of commands separated by semi-colon (;) which you want to show under cascading menu. You can’t add any program shortcut directly. First you’ll need to give any desired command name in this list and after that you’ll need to register it using PART 2 so that it can start working.
    
    __Example__  
    Suppose you want to add Notepad and Calculator shortcuts under __SubCommands__. In this case, you’ll need to set following as __SubCommands__ value:
    ````cmd
    notepad;calc ;this name can be anything. It is only needed to reference in latter phase
    ````
    PS: If you want to put a separator between menus, just use Pipe symbol (|) between commands. For example, notepad;|;calc
    
    __Icon__ String value can be used to show an icon for your cascading menu. (Value => path to exe)
    
    __Position__ String value can be used to define the position of cascading menu in the context menu. By default the cascading menu is shown in the middle but you can set its position at Top or Bottom with the help of “Position” String value.
    
_(Once you have added the program shortcuts to cascading menus using above processes, you’ll need to register the commands mentioned in __SubCommands__ String value using following method)_

5. Go to following key:  
    ````cmd
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\CommandStore\Shell
    ````  
6. Under this key, we’ll need to create new keys for each command mentioned in __SubCommands__ String value. (example: notepad and calc)

7.  Once you create the key, select it and in right-side pane set value of __(Default)__ to the name which you want to show in cascading menu. For example set its value to Notepad or Calculator or any other desired string.

8. If you also want to show an icon for it, create a new String value with the name icon and set its value to program’s EXE file path or any other desired icon. For example, to show Notepad icon for Notepad shortcut, you can set value of Icon to notepad.exe

9. Now final step! Create a new key under the recently created keys, e.g. notepad or calc and give it name __command__.

    Click on it and in right-side pane, set value of __(Default)__ to the path of your desired program’s EXE file. For example, if you want to open Notepad when you click on “Notepad” entry in cascading menu, set value of “Command” to notepad.exe