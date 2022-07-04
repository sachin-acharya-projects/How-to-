# Customize Command Prompt on Startup
______________________________________
> Redirects  
> [Informations](#informations)   
> [Process](#process)  
_______________________________________
## Informations
These are the brief methodology on how to customize command prompt. On starting command prompt, default looks on cmd would look like `[drive]:\path\from\which\cmd\is\running>` which is kinda boring and we can change that behaviour of cmd permanently (can be changed back) like, even after the computer has been booted, our custom settings won't be changed.

## Process
What is want to do is, echo 
````
    ([current day date-time]) [current path] | [my name]: 
````
instead of plain old echo.
For that, we need to follow some of the steps as shown below

* Type ````regedit```` in RUN or Start Menu Search box and press Enter. It’ll open Registry Editor.  

* Now go to following key:  
````
    Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Command Processor
````

* Now we’ll need to create a new string value under __Command Processor__ key. Right-click on __Command Processor__ key and select __New -> String Value__. Give it the name, __Autorun__

* Set the value of this string value with the command you want to when command prompt is launched
For our case
````
prompt ($D $T) $P $B Sachin Acharya: 
````
we can change the value of any desired cmd-command and can also run multiple command by separting each with &&
for example, we I want what I want with green color, I would replace value with
````
color 02 && prompt ($D $T) $P $B Sachin Acharya: 
````
> For more information about color and prompt run color /? and prompt /? command on cmd

#### Bonus Tip
To create alias in windows terminal

````
doskey alias=command
````
