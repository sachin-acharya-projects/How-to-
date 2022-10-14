# Uncategorized Informations

**Reference Links**

1. [Creating Self-Signed Certificates for applications](#N1)
2. [Creating Alias in Windows](#N2)
3. [Reference to SSH](#N3)
4. [Programming Task Scheduler](#N4)
5. [Change Style of Top Panel (Ubuntu)](#N5)
6. [All About Symbolic Links](#N6)
7. [How run script on startup](#N7)
______________________________________________
<div id='N1'></div>  

* Create a Self-Signed Certificates for applications (*.exe)

    [Visit This Link](https://mmus.me/blog/certificates/)

    *Commands used in the tutorial -- Run Powershell with UAC and run following commands*

    ````powershell
    $cert = New-SelfSignedCertificate -DnsName test.name.com -CertStoreLocation cert:\LocalMachine\My -type CodeSigning

    $pwd = ConvertTo-SecureString -String "MyPassword" -Force -AsPlainText

    Export-PfxCertificate -cert $cert -FilePath mycert.pfx -Password $pwd
    ````

    *And Then*

    ````powershell
    signtool.exe sign /f mycert.pfx /p MyPassword my_application.exe
    ````

    [Download Signtool](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk/) and add it to PATH

    **Note to obtain signtool.exe without installing the complete Windows SDK. Download the ISO for the Windows SDK from the link above. Mount the ISO and open up the Installers folder and install the appropriate msi for Windows App Certification Kit.**
    
    **In my case I installed Windows App Certification Kit x64-x86_en-us.msi, which installs the executable to C:\Program Files (x86)\Windows Kits\10\App Certification Kit\signtool.exe**

___________________________________________________________________
<div id='N2'></div>  

* Creating Alias in Windows
    ````bash
    alias alias_name=command; "sequence_of_task" # This is for Linux
    ````

    ````powershell
    doskey alias_name=command; "sequence_of_task" REM This is for Windows
    ````
____________________________________________
<div id='N3'></div>

* Reference to SSH

    [https://theitbros.com/ssh-into-windows/](https://theitbros.com/ssh-into-windows/)  
    [https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

____________________________________________________
<div id='N4'></div>

* Program Task Scheduler

    [Programatic way of using Task Scheduler](https://medium.com/@ajay.bile007/programmatic-way-of-creating-task-in-windows-task-scheduler-8673c5d5b897)

_____________________________________________________
<div id='N5'></div>

* Change Style of Top Panel in Ubuntu
    * First Download Gnome Tweaks and Gnome Shell Extensions and also the Extension Manager
        ````bash
        sudo apt install gnome-tweaks gnome-shell-extensions gnome-shell-extension-manager
        ````
    * Find Extension Manager from application drawer and launch it.
    * Now, in `browse` tab, search for the extension `User themes` then install and enable it.
    * Now, create a folder as shown below
        ````bash
        mkdir -p ~/.local/share/themes/myTheme/gnome-shell/ # myTheme can be any name you want for your theme
        ````
    * Now change into the newly created directory and create new file `gnome-shell.css`
        ````bash
        touch gnome-shell.css # path: ~/.local/share/themes/myTheme/gnome-shell
        ````
    * Now open this file with your prefered text-editor and enter the following line  
        _Edit file_
        ````bash
        gedit gnome-shell.css
        ````

        _Add Line_
        ````css
        @import url("resource:///org/gnome/theme/gnome-shell.css");
        ````

        __We are importing everything from the default Gnome Adwaita theme. Change as you wish.__
    * Now overide the property using `<stage>` or `<#panel>` selector
        ````css
        stage {
            font-size: 9pt;
        }
        ````

        *Or*

        ````css
        #panel {
            padding: 30px;
        }
        ````
    
    * After saving the file, run tweak we previously installed and under the section `appearance`, choose your new theme `myTheme` as shell-theme
        ````css
        Appearance > Shell > myTheme ... done
        ````
_____________________________________________________
<div id='N6'></div>

* Create a Symbolic Link/Shortcut in Ubuntu  
    ````bash
    ln -s /path/to/source /path/to/output # creates relative link
    ````

    ````bash
    ln -s "$(realpath /path/to/source)" /path/to/output # creates absolute link
    ````

* Read absolute filepath
    ````bash
    readlink -f filename
    ````

* Convert Every Symbolic Link in directory Absolute to Relative
    ````bash
    symlinks -c /path/to/directory
    ````

___________________________________
<div id="N7"></div>

* How to run file on system boot  
    * Using Crontab  
        ````bash
        crontab -e #edit
        # and add this line when in editor 
        # @reboot  /home/user/startup.sh
        # search crontab for more details
        ````
    
    * Using init.d directory
        ````bash
        # Copy file to /etc/init.d/ folder and if it still doesnot work
        # Create a symbolic link to the folder /etc/rc.d/
        # Like so
        ln -s /etc/init.d/start_my_app /etc/rc.d/
        # Please note that on the latest versions of Debian, this will not work as your script will have to be LSB compliant (provide at least the following actions: start, stop, restart, force-reload, and status)
        ````

    _(In both cases, make sure the scripts are executable and has a seebang at the top of the file)_

    _(seebang)_
    ````bash
    #!/bin/bash
    ````

    _(executable)_
    ````bash
    chmod +x filename
    ````
