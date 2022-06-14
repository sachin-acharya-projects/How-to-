# Create Custom Protocol in windows
____________________

Follow the steps to create a custom protocol

#### Steps
1. Select KEY HKCR `Computer\HKEY_CLASSES_ROOT`

2. Create new KEY inside this KEY name it as you like, which will be your protocal name (eg: http)

3. Create new String Value __New > Key Value__ and name is `URL Protocol`

4. Put `URL:name Protocol` as value for default (eg. URL:cmd Protocol for create protocol cmd)

5. Now create three nested new key under current key __shell > open > command__

6. Now insert value for __command > default__ as you wish which will be executed whenever used the protocol