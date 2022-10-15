### 😮‍💨 Pretty a heavy list

⬇️ 查询命令
```shell
man
man man
```
⬇️ 获取 root 权限
```shell
sudo #一次性使用
sudo su #一直使用 root 权限 之后想要退出输入 exit 然后回车
```
⬇️ 清空命令记录
```shell
clear 
```
⬇️ create a folder
```shell
mkdir
```
⬇️ change the directory
```shell
cd <folder name>
```
⬇️ remove the directory only work if in the folder
```shell
rmdir <folder name>
```
⬇️ printout working directory
```shel
pwd
```
⬇️ create files
```shell
touch <filename>
```
⬇️ list all the files and folders in the current directory
```shell
ls
```
⬇️ ⭐ find the location of file
```shell
locate <filename>
```
> The bonus round is that if you know that the file does exist but you get a blank result then run `sudo updatedb` which will index all the files in the file system then run your `locate` again. If you do not have `locate` available to you, you can install it using this command `sudo apt install mlocate` 

⬇️ ⭐ moving file from on location to another
```
mv <filename> <to filepath>
```
⬇️ ⭐ change file name
```shell
mv <old filename> <new filename>
```
⬇️ remove file or directory
```shell
rm <filename> #remove file
rm -R <directory> #remove by recursively work throung a folder or locaiton
rm -R -f <directory> #force remove by recursively...
```
⬇️ ⭐ copy file
```shell
cp <filename> <directory>
```
⬇️ ⭐ add content to file
```shell
echo "Hello World" > <filename> #change content
ehco "commands are fun" >> <filename> # 
```
⬇️ ⭐ concatenate: see the contents inside the file
```shell
cat <filename>
```
⬇️ ⭐ search file for a specific work
```shell
cat <filename> | grep "world"
```
⬇️ ⭐ commands history
```shell
history #show commands we have run prior
history !3 # choose the 3rd command in the list⬆️
history -c #remove the history
history | grep "Command" # search for somethin specific
```
⬇️ date and time to each command
```shell
#date and time to each command
HISTTIMEFORMAT="%d-%m-%Y %T "
#You can easily add to your bash_profile:
echo 'export HISTTIMEFORMAT="%d-%m-%Y %T "' >> ~/.bash_profile
#So as useful to allow the history file to grow bigger:
echo 'export HISTSIZE=100000' >> ~/.bash_profile
echo 'export HISTFILESIZE=10000000' >> ~/.bash_profile
```
⬇️ change your password
```shell
password
```
⬇️ add new users to our system
```shell
sudo useradd NewUser
```
⬇️ Creating a group
```shell
sudo groupadd <group name>
#add our new user to that group
sudo usermod <user name> -a -G <group name> #`-a` is add and `-G` is group name
```

# Pressions
| `---`       | `--X`     | `-W-`       | `-WX`    | `R--`       | `R-X`     | `RW-`       | `RWX`   |
| ----------- | --------- | ----------- | -------- | ----------- | --------- | ----------- | ------- |
| ~~Read~~    | ~~Read~~  | ~~Read~~    | ~~Read~~ | Read        | Read      | Read        | Read    |
| ~~Write~~   | ~~Write~~ | Write       | Write    | ~~Write~~   | ~~Write~~ | Write       | Write   |
| ~~Execute~~ | Execute   | ~~Execute~~ | Execute  | ~~Execute~~ | Execute   | ~~Execute~~ | Execute |
🌰 ⬆️ ⬇️ 
```shell
ls -al <filename>
#you can see the 3 groups mentioned above, user and group have read & write but everyone only has read.
-rw-r--r--  1 wuzhenquan  staff  21 Oct  3 23:35 <filename>
```

# 后面几个命令比较难理解 好像也没用过 就先忽略 
