# wsl_clash_proxy
在适用于Linux 的Windows 子系统中通过clash配置代理
- 打开Clash for Windows 的Allow LAN 开关
![image](https://github.com/user-attachments/assets/2fd37a06-3335-485f-a255-a8990bd35431)

- 回到主目录
```
cd ~
```
- 创建文件`.proxyrc`
```
#!/bin/bash
hostip=$(ip route | grep default | awk '{print $3}')
export https_proxy="http://${hostip}:7890"
export http_proxy="http://${hostip}:7890"
```
- 赋予执行权限
```
chmod 755 .proxyrc
```
- 启动代理
`source ~/.proxyrc`
-  (可选,开机启动代理)打开文件`~/.bashrc`，在后面添加
```
if [ -f ~/.proxyrc ]; then
    source ~/.proxyrc
fi
```
