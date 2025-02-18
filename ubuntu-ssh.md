# Ubuntu配置ssh
Ubuntu git 使用ssh克隆远程仓库报错：
```
Unable to negotiate with **** port 22: no matching host key type found. Their offer: ssh-rsa
```
解决方案：在.ssh路径配置config
config:
```
Host *
HostkeyAlgorithms +ssh-rsa
PubkeyAcceptedKeyTypes +ssh-rsa
```
另，win中查看wsl存储文件：```\\wsl$```