# Uncategorized Informations

**Reference Links**

1. [Creating Self-Signed Certificates for applications](#N1)
2. [Creating Alias in Windows](#N2)
3. [Reference to SSH](#N3)
4. [Programming Task Scheduler](#N4)
______________________________________________
<div id='N1'></div>  

* Create a Self-Signed Certificates for applications (*.exe)

    [Visit This Link](https://mmus.me/blog/certificates/)

    *Commands used in the tutorial -- Run Powershell with UAC and run following commands*

    ````
    $cert = New-SelfSignedCertificate -DnsName test.name.com -CertStoreLocation cert:\LocalMachine\My -type CodeSigning

    $pwd = ConvertTo-SecureString -String "MyPassword" -Force -AsPlainText

    Export-PfxCertificate -cert $cert -FilePath mycert.pfx -Password $pwd
    ````

    *And Then*

    ````
    signtool.exe sign /f mycert.pfx /p MyPassword my_application.exe
    ````

    [Download Signtool](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk/) and add it to PATH

    **Note to obtain signtool.exe without installing the complete Windows SDK. Download the ISO for the Windows SDK from the link above. Mount the ISO and open up the Installers folder and install the appropriate msi for Windows App Certification Kit.**
    
    **In my case I installed Windows App Certification Kit x64-x86_en-us.msi, which installs the executable to C:\Program Files (x86)\Windows Kits\10\App Certification Kit\signtool.exe**

___________________________________________________________________
<div id='N2'></div>  

* Creating Alias in Windows
    ````
    alias alias_name=command; "sequence_of_task" # This is for Linux
    ````

    ````
    doskey alias_name=command; "sequence_of_task" # This is for Windows
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
