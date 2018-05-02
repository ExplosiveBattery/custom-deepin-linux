# Custom deepin linux
### 内核定制（好处，教程）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=155660&extra=  
### 开机动画
见plymouth文件夹  
### 切换桌面壁纸（脚本，内存泄露问题）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=155474&extra=  
### 桌面美化(conky，类似于windows下的水滴桌面)
见conky文件夹  
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
