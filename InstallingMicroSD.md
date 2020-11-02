# Installing image on Micro-SD

## Partitions in MicroSD

- Boot Partition FAT32
- Data Partition Ext4 (Linux)
- Un espacio vacío

## Writing the image on MicroSD

- Download and install [Etcher](https://www.balena.io/etcher/).
- Download the image.
- Execute Etcher and install image on microSD.


## Deleting everything in MicroSD

- Overwriting the image on MicroSD.
- Using [MiniTool Partition Wizard](https://www.partitionwizard.com/free-partition-manager.html) for Windows or [GParteden](https://gparted.org/) for Linux.

## Reading or Writing data on Linux partition (Ext4)

On Windows use [DiskInternals Linux Reader](https://www.diskinternals.com/thanks/?utm_source=exefile&utm_medium=linux_reader&utm_campaign=install&dd=https%3A%2F%2Feu.diskinternals.com%2Fdownload%2FLinux_Reader.exe) for explore the linux partition. Other option can be [ext2fsd](http://www.ext2fsd.com/?page_id=25)

# Connecting to IoT2040 using SSH

## SSH Protocol - Using Putty
- Change IP to 192.168.200.2 (ethernet) from you computer using Control Panel.
- Install Putty and launch.
- Configure Putty for connect to IoT IP 192.168.200.1 using 22 port.
- Click on Open and after confirm fingerprint doing click on yes.
- Enter the user name "root" for the login and confirm the entry with ENTER. If don't have error, you are conected to device.

## SCP/SFTP Protocol - Using WinSCP
- Download and install WinSCP.
- Start WinSCP.
- Enter the IP and port of IoT2040 (By default IP is 192.168.200.1 a Port is 22)
- Enter the username "root"
- Left the password empty.
- Click on "Login"
- Confirm the fingerprint of the IoT, click on "Yes".

# Change configuration of IoT2040

## Custom the IP address of IoT2040 using iot2000setup

- Connect to device using ssh.
- Enter "iot2000setup" and wait by interface.
- Select "Networking" and press ENTER.
- Select "OK" using TAB key, and press ENTER.
- Change the IP of eth0 to 192.168.0.32
- Confirm the changes using the "OK" field.

If you finished without issues, the new ip of your iot2040 is 192.168.0.32.

## Custom the IP address of IoT2040 using /etc/network/interfaces
- Open file configuration typing the command:  nano /etc/network/interfaces
- Change the IP, like you are in the notebook.
- You can exit the program again with key combination Ctrl+X. Any changes can be accepted with Y or discarded with N.



