# 安装wsl和docker配置

## 安装wsl以及docker需要依赖
- 启用或关闭 Windows 功能中安装 ”Hyper-V“、"适用于 Linux 的 Windows 子系统"、”虚拟机平台“，点击确定下载后重启

## 安装wsl
```
wsl --update
wsl --set-default-version 2
```
- 之后Microsoft Store上安装 Ubuntu 22.04.5 LTS
## 安装docker
- 安装Docker Desktop
- 不使用wsl2引擎（会报错）
- Docker Desktop中设置```General->Expose daemon on tcp://localhost:2375 without TLS```
## 配置wsl中docker
```
sudo apt-get remove docker docker-engine docker.io
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get install docker-ce
```
```
export DOCKER_HOST=tcp://localhost:2375
```
```
sudo update-alternatives --config iptables
```
输入这个后会显示以下内容
```
  Selection    Path                       Priority   Status
------------------------------------------------------------
* 0            /usr/sbin/iptables-nft      20        auto mode
  1            /usr/sbin/iptables-legacy   10        manual mode
  2            /usr/sbin/iptables-nft      20        manual mode

Press <enter> to keep the current choice[*], or type selection number: 
```
这里输入1，然后再次启动docker即可
```
sudo service docker start
```