## Managing Ubuntu & Software
apt package manager - for updates and software installtaion
```shell
sudo apt-get udpate
```

uses of software **figlet**
```shell
sudo apt install figlet #install
figlet 90DaysOfDevOps
sudo apt remove figlet #uninstall
```
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day16_Linux4.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day16_Linux4.png) 
## File System Explained
> Linux is made up of configuration files, if you want to change anything then you change these configuration files.

```shell
cd /
ls
```
⬆️⬇️
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day16_Linux8.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day16_Linux8.png) 
### `/bin`
Short for binary
The bin folder is where our binaries that your system needs, executables and tools will mostly be found here.
### `/boot`
All the files your system needs to boot up. How to boot up, and what drive to boot from.
### `/dev`
You can find device information here, this is where you will find pointers to your disk drives `sda` will be your main OS disk.
### `/etc`
Short for etcetera.
[Linux directory structure explained:/etc folder](https://www.linux.com/training-tutorials/linux-directory-structure-explainedetc-folder/#:~:text=ETC%20is%20a%20folder%20which,is%20having%20some%20interesting%20history.)
Likely the most important folder on your Linux system, this is where the majority of your configuration files are.
### `/home`
this is where you will find your user folders and files. We have our vagrant user folder. This is where you will find your `Documents` and `Desktop` folders that we worked in for the commands section.
```shell
cd ~ #take you to your user home directory
```
### `/lib`  
find the shared libraries
### `/media`  
This is where we will find removable devices.
### `/mnt` 
temporary mount point.
### `/opt` 
Optional software packages
### `/ proc`
Kernel & process information, similar to `/dev` 
### `/root` 
The home folder for root.
### `/run`
Placeholder for application states.
### `/sbin`
Sudo bin, similar to the bin folder but these tools are intended for elevated superuser privileges on the system.
### `/tmp`
temporary files.
### `/usr`
 If we as a standard user have installed software packages it would generally be installed in the `/usr/bin` location.
### `/var`
 Our applications get installed in a `bin` folder. We need somewhere to store all of the log files this is `/var` 
## Storage 
-   `lsblk` Short for LiSt BLocK devices. `sda` is our physical disk and then `sda1, sda2, sda3` are our partitions on that disk.
	[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day16_Linux25.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day16_Linux25.png) 
-   `df` gives us a little more detail about those partitions, total, used and available. You can parse other flags here I generally use `df -h` to give us a human output of the data.
	[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day16_Linux26.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day16_Linux26.png)
接下来主要讲的是如何将一个新的磁盘挂载到 filesystem 上
- format a new disk: `sudo mkfs -t ext4 /dev/sdb`
	- mkfs: short for **make file system** 
	- ext4: short for **Fourth extended filesystem**
- create a directory: `sudo mkdir NewDisk`
- mount the disk to that location: `sudo mount /dev/sdb newdisk`
- add this disk to persist: add this disk to our `/etc/fstab` configuration file （如果不设置的话重启了就要重新 mount（不过数据还在））