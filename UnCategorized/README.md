______________________________________________
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

* Creating Alias in Windows
    ````
    alias alias_name=command; "sequence_of_task" # This is for Linux
    ````

    ````
    doskey alias_name=command; "sequence_of_task" # This is for Windows
    ````