## SSH
这部分像是从这个视频里记录下来了，看这个视频就好了 [The Beginner's guide to SSH](https://www.youtube.com/watch?v=2QXkrLVsRmk) 
### Confirming SSH is running
`sudo systemctl status ssh`: 检查 SSH 是否 configured on our machine
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day18_Linux3.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day18_Linux3.png) 
`sudo apt install OpenSSH-server`: 如果还没有安装的话安装一下
`sudo ufw allow ssh`: make sure SSH is allowed if the firewall is running

### Remote Access

#### By SSH Password

不安全 也麻烦

文中使用的是 GUI 工具 - putty

#### By SSH Key
provide a key pair ➡️ both the client and server know that this is a trusted device
- identification key
- public key
steps: 
1️⃣ create a key pair ⬇️ :
```shell
ssh-keygen -t ed25519
```
⬆️ what is `ed25519` ➡️ [cryptography](https://en.wikipedia.org/wiki/EdDSA#Ed25519) 
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day18_Linux7.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day18_Linux7.png) 
2️⃣ link key pair with remote Linux VM
```shell
ssh-copy-id <server IP>@<server IP>
```
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day18_Linux8.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day18_Linux8.png) 3️⃣ test our connection

```shell
ssh <server name>@<server IP>
```
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day18_Linux9.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day18_Linux9.png) 
4️⃣ 现在还需要输入 passphrase 才能连接，如何 no passwords at all？
```shell
sudo nano /etc/ssh/sshd_config
```
可以看到 `PasswordAuthentication yes` 这一行被 comment 掉了，
- uncomment 回来并且把 `yes` 改为 `no`
- 重启 ssh: `sudo systemctl reload sshd` 

## Setting up a Web Server 
==这个 LAMP stack 其实有点 old school 了 可以考虑更加现代的 Web Server==
%%🤩 比如我最爱的 deno 🦕%%
LAMP stack
- Linux Operationg System
- Apache Web Server (??? 调研一下会不会太 old school 了)
- mySQL database
- PHP(为啥不用 Go 🦦 ?)
#### Apache2
```shell
# 1️⃣ 安装
sudo apt-get install apache2 
# 2️⃣ 确认是否安装成功
sudo service apache2 restart
# 3️⃣ 打开浏览器，通过这个 VM 的 IP 访问
```
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day18_Linux10.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day18_Linux10.png)
#### MySQL
目的： storing our data for our simple data
```shell
#安装
sudo apt-get install mysql-server
```
#### PHP
目的：use PHP to interact with a MySQL database
```shell
#安装
sudo apt-get install php libapache2-mod-php php-mysql
```
1️⃣ apache 的 index.html 替换成 index.php
```shell
sudo nano /etc/apache2/mods-enabled/dir.conf
```
然后把 index.php 放到 index.html 的前面
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day18_Linux11.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day18_Linux11.png)
2️⃣ 重启 apache：`sudo systemctl restart apache2` 
3️⃣ 确认系统是否 configured correctly for PHP
open a blank file in nano
```shell
sudo nano /var/www/html/90Days.php
```
在文件中添加一下文本
```php
<?php
phpinfo();
?>
```
打开浏览器访问 `http://192.168.169.135/90Days.php` 可以看到以下内容
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day18_Linux12.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day18_Linux12.png) 
#### WordPress Installation
[How to install WordPress on Ubuntu with LAMP](https://blog.ssdnodes.com/blog/how-to-install-wordpress-on-ubuntu-18-04-with-lamp-tutorial/) 

