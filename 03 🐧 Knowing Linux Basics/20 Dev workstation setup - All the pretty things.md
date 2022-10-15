作者还做了一个视频 [Linux Desktop Customisation Setup](https://youtu.be/jeEslAtHfKc)
作者这边主要介绍的是 Ubuntu VM 上的 Linux desktop
## dotfiles
*⛏️ dig into dotfiles*
dotfiles 是 configuration files for your Linux system and applications.
不仅 customise and make your desktop look pretty
而且 help you with productivity
Each dotfile starts with a `.` （比如.bashrc 和 .bash_profile)
怎么更改 shell ？➡️  修改 `.zshrc` 文件
## ZSH
ZSH has some benefits over bash.
- interactive Tab completion
- automated file searching,
- regex integration
- advanced shorthand for defining command scope
- a rich theme engine.
安装 ➡️ `sudo apt install zsh`
将默认 shell 改成 zsh ➡️ `chsh -s $(which zsh)` 
查看当前时哪种 shell: `which $SHELL`
## OhMyZSH
[ohmyzsh](https://ohmyz.sh/) 
安装 `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
推荐两个 pulgins
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
nano ~/.zshrc
#⬇️ edit the plugins to now include
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```
## [Gnome extensions](https://extensions.gnome.org/)
- Caffeine
- CPU Power Manager
- Dash to Dock
- Desktop Icons
- User Themes
## Software Installation
- VSCode
- azure-cli
- containerd.io
- docker
- docker-ce
- google-cloud-sdk
- insomnia
- packer
- terminator
- terraform
- vagrant
### [Dracula theme](https://draculatheme.com/) 






