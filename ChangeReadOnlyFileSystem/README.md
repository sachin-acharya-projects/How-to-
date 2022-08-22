# Change ReadOnly File-System to Read-Write File-System
_______________________________________________________

Follow the following process to achive the goal.

1. Open a terminal and run following command.

````
sudo fdisk -l # Alread root? omit sudo
````

2. Find your desired drive in the output

It appears something like this

_@ represents number_
````
Device         Start       End   Sectors    Size    Type
/dev/sda1       @           @       @        @M     EFI System
/dev/sda2       @           @       @        @M     Microsoft reserved
/dev/sda3       @           @       @        @G     Microsoft basic data
/dev/sda4       @           @       @        @G     Microsoft basic data
/dev/sda5       @           @       @        @M     Windows recovery environment
````

3. Select your device (Microsoft basic data) -- /dev/sda@

4. Run following command to change to read-write mode
````
sudo ntfsfix your device # /dev/sda4
````

_Use this command for all drive you wants -- must be of type Microsoft Basic Data_

5. Finally unmount the drive
