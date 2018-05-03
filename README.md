## 基本操作
### 内核定制（好处，教程）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=155660&extra=  
### 开机动画
见plymouth文件夹  
### 切换桌面壁纸（脚本，内存泄露问题）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=155474&extra=  
### 桌面美化(conky，类似于windows下的水滴桌面)
见conky文件夹  
### 设置开机自动执行什么(包含开机应用自启动，比如说conky，壁纸自动切换)
见autostart文件夹
### 配合conky的show desktop
https://bbs.deepin.org/forum.php?mod=viewthread&tid=155656&extra=  
程序会读取~/.toggleconfig中的每一行作为一个顶级窗口名，如果存在同样的窗口名则不会被ShowDesktop（win+d按键）影响
### 钉宫语音包
https://bbs.deepin.org/forum.php?mod=viewthread&tid=154264
### topbar(顶栏)
https://bbs.deepin.org/forum.php?mod=viewthread&tid=141816
### 透明化dock(底栏)
https://bbs.deepin.org/forum.php?mod=viewthread&tid=149493
### 应用图标定制
见icons文件夹
### 无线网卡工作模式
`iwconfig`  
如果发现有一行Power Management:powersave说明网卡工作在低功耗，emmm，我觉得这可能是我信号不好的原因  
`sudo iw dev wlp2s0 set power_save off`  

<p>&nbsp;</p><p>&nbsp;</p>

## 重要应用（我觉得）
### docker
https://github.com/ExplosiveBattery/docker  
仓库中有两个pdf，一个是介绍docker，一个是如何安装docker，我的deepin安装使用了：  
`wget -qO- https://get.docker.com/ | sh` 一条命令解决  
`cat /etc/debian_version` 可以看到deepin15.5是debian 8.0 sid（也就是jessie unstable）  
### katoolin
https://github.com/LionSec/katoolin  
自己选择部分工具安装即可，不推荐使用kali docker，因为docker不适合会变动的东西，比如部分经常有更新的软件：metasploit，nmap  
