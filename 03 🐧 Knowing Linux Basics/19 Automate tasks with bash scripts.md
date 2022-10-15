****> we should learn shell/bash scripting to work alongside our automation tools and for ad-hoc tasks.

## Getting started
the only real way to learn is through doing
figlet:可以在命令行里面把字体打得很花

⬇️ 90DaysOfDevOps.sh
```shell
#!/usr/bin/bash #your bash binary path
#!/usr/bin/env bash
mkdir 90DaysOfDevOps
cd 90DaysOfDevOps
touch Day19
ls
```
⬆️ 执行上述代码
```shell
./90DaysOfDevOps.sh
```
🚨 出现了权限问题
```shell
./bashHelloWorld.sh
zsh: permission denied: ./bashHelloWorld.sh
```
看看这个文件的权限情况
```shell
ls -al 90DaysOfDevOps.sh
```
发现只有读写的权限
```shell
-rw-r--r--   1 wuzhenquan  staff    54 Oct 13 17:47 90DaysOfDevOps.sh
```
修改这个文件的权限
```shell
chmod +x 90DaysOfDevOps.sh
```
## Variables
```shell
ChallengeName="90DaysOfDevOps"
TotalDays=90

echo "Hey everyone, welcome to the $ChallengeName"
echo "We have $TotalDays days to learn something about something"
```
## Conditionals
⬇️ the options
| `eq`  | `ne`        | `gt`           | `ge`                       | `lt`        | `le`                    |
| ----- | --------- | ------------ | ------------------------ | --------- | --------------------- |
| equal | not equal | greater than | greater than or equal to | less than | less than or equal to |
```shell
#!/bin/bash 
# This script is to demonstrate bash scripting!

# Variables to be defined

ChallengeName=#90DaysOfDevOps
TotalDays=90

# User Input

echo "Enter Your Name"
read name
echo "Welcome $name to $ChallengeName"
echo "How Many Days of the $ChallengeName challenge have you completed?"
read DaysCompleted

if [ $DaysCompleted -eq 90 ]
then
  echo "You have finished, well done"
elif [ $DaysCompleted -lt 90 ]
then
  echo "Keep going you are doing great"
else
  echo "You have entered the wrong amount of days"
fi
```
⬇️ file conditions
| `-d file`             | `-e file`     | `-f file`                   | `-g file`                   | `-r file`          | `-s file`                  | 
| ------------------- | ----------- | ------------------------- | ------------------------- | ---------------- | ------------------------ |
| file is a directory | file exists | provided string is a file | group id is set on a file | file is readable | file has a non-zero size |

```shell
FILE="90DaysOfDevOps.txt"
if [ -f "$FILE" ]
then
  echo "$FILE is a file"
else
  echo "$FILE is not a file"
fi
```
## Example
#### Before code
- `touch create_user.sh`
- `chmod +x create_user.sh`
- `nano create_user.sh`
#### Code
linux: `#! /usr/bin/bash` macos: `#! /bin/bash`
这里写 macos 的
```shell
#! /usr/bin/bash

echo "What is your intended username?"
read  username
echo "What is your password"
read  password #read -s password 可以不显示密码
```
**1️⃣ A user can be passed in as a command line argument**
```shell
echo "$username user account being created."
```
**2️⃣ A user is created with the name of the command line argument**
option `-m` ➡️ create the user home 📥 `/home/<username>`
```shell
sudo useradd -m $username
```
check if created successfully ➡️ `awk -F: '{ print $1}' /etc/passwd` 
**3️⃣ A password can be parsed as a command line argument**
```shell
sudo chpasswd <<< $username:$password
```
**4️⃣ A message of successful account creation is displayed**
```shell
echo "The account for $username has successfully been created"
```

#### Full Code
```shell
#! /bin/bash

echo "What is your intended username?"
read  username
echo "What is your password"
read  password
echo "$username user account being created."
sudo useradd -m $username
sudo chpasswd <<< $username:$password
echo "The account for $username has successfully been created"
```
执行上述脚本 ➡️ 输入 username ➡️ 输入 password
检查是否创建成功了：`su - <username>` ➡️ 输入 password ➡️ 执行`whoami` ➡️ 打印出 username

删除用户：sudo userdel test_user

[Example Script](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Linux/create-user.sh) 