# How to ByPass UAC using Task Scheduler
___________________

1. Start __Run (Win + R)__ and type in `taskschd.msc` and hit __Enter__.
    This will start task scheduler

2. Select the Task Scheduler Library folder and on the Actions pane click on New Folder… action (_Name it as you wish_).

3. Select the newly created folder and on the Actions pane click on Create Task… action.

4. In the General tab of the Create Task window type in the name of the task. Remember the name as you’ll need it later. A description is optional but recommended. Under the security options check the Run with highest privileges checkbox.

5. Switch to the Actions tab and click on the New… button. Keep the action set to Start a program and browse for the program you want to run without the UAC. A new action should appear in the actions list after you click on the OK button.

6. After you’ve finished setting up your task click on the OK button and a new task should appear in your previously created folder with the status of Ready. You can now close the Task Scheduler.

7. To run the task you’ll have to create a shortcut. Right-click anywhere in the __File Explorer__ and select __New > Shortcut__. In the Create Shortcut window enter the following text. You should keep the quotes otherwise, the task won’t run. Keep in mind that the task folder and the task are separated with a backslash `\`.
    ````
    C:\Windows\System32\schtasks.exe /run /tn "YourFolder\YourTask"
    ````