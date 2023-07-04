# Create Custom Protocol in windows
____________________

Follow the steps to create a custom protocol

### Steps
To create a custom protocol handler in Windows, such as `sachin://`, you need to modify the Windows Registry. Here's a step-by-step guide to help you set it up:

1. **Choose a unique protocol name**: In this case, we'll use `sachin` as the protocol name.
2. **Create a new key in the Windows Registry**: Open the Registry Editor by pressing Win + R and typing regedit. Navigate to the following path:
    ```regedit
    HKEY_CLASSES_ROOT
    ```
3. **Create new Key**: Right-click on `HKEY_CLASSES_ROOT` and select `New > Key`. Name the key as your chosen protocol name (e.g., `sachin`).
4. **Set the protocol's default value**: Inside the newly created key, right-click and select `New > String Value`. Name this string value as `URL Protocol`. Leave the value empty.
5. **Associate the protocol with an application**: Create another key inside the protocol key, and name it `shell`. Under the `shell` key, create another key with the name of the action you want to perform, such as `open`. Inside the `open` key, create another key called `command`.
6. **Set the default value for the command key**: Double-click the `(Default)` value inside the `command` key and set the value to the `command` that should be executed when the protocol is triggered. For example, if you want to open VLC media player and play the specified file, set the value to:
    ```
    "C:\Path\to\VLC\vlc.exe" "%1"
    ```
    Ensure you replace "C:\Path\to\VLC\vlc.exe" with the actual path to your VLC media player executable.
