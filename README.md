在适用于Linux 的Windows 子系统中通过clash配置代理
# wsl_clash_proxy
1 打开clash for windows 的allow lan 开关
2 运行`cd ~`回到主目录
3 建立文件`.proxyrc`
写入
```
#!/bin/bash
hostip=$(ip route | grep default | awk '{print $3}')
export https_proxy="http://${hostip}:7890"
export http_proxy="http://${hostip}:7890"
```
