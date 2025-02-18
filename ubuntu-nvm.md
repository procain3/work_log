# Ubuntu中安装nvm
## nvm的安装
``` bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```
之后配置环境变量：
``` bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
配置好后刷新重启Ubuntu
``` bash
source ~/.bashrc
source ~/.profile
```
## 设置软链接启动win中浏览器
设置软连接
``` bash
cd /usr/bin
sudo ln -s /mnt/c/Program\ Files/Google/Chrome/Application/chrome.exe mschrome
sudo update-alternatives --install /usr/bin/x-www-browser x-www-browser /usr/bin/mschrome 200
```
设置环境变量
``` bash
# 临时设置（当前会话有效）
export BROWSER="/usr/bin/mschrome"
npm login --registry=...

# 永久设置（写入 ~/.bashrc）
echo 'export BROWSER="/usr/bin/mschrome"' >> ~/.bashrc
source ~/.bashrc
```