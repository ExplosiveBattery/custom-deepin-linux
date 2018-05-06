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
这个帖子楼主的包有点不完善，拉倒后面有人发了比较好的
### topbar(顶栏)
https://bbs.deepin.org/forum.php?mod=viewthread&tid=141816
### 透明化dock(底栏)
https://bbs.deepin.org/forum.php?mod=viewthread&tid=149493  
自定义dock大小：
https://jingyan.baidu.com/article/f7ff0bfc3f49132e26bb1338.html （还可以使用gsettings命令）
### 应用图标定制
见icons文件夹
### 无线网卡工作模式
`iwconfig`  
如果发现有一行Power Management:powersave说明网卡工作在低功耗，emmm，我觉得这可能是我信号不好的原因  
`sudo iw dev wlp2s0 set power_save off`  
### 定时任务
cron了解一下，相关命令crontab（相关参数-e,-l），相关文件
### 自定义手势
手势有触摸板手势 以及 鼠标手势（相当于点着鼠标左键的触摸板手势）  
我幻想着能够在触摸板上画一个五角星，电脑就会关机....emmm...妥妥的利器  
触摸板手势： xSwipe（老久系统使用），Fusuma，Touchégg  
鼠标手势：Easystroke（Windows中WGestures）
我当时设置了Easystroke的五角星关机，每次关机...emmm....按着触摸板左键，再画一个五角星
### 屏保
https://www.deepin.org/2012/09/17/install-xscreensaver-in-linux-deepin/  
推荐屏保主题：cmatrix（装逼利器）
### 主题
目前为止好看的主题：  
https://github.com/horst3180/Arc-theme  
https://github.com/adapta-project/adapta-gtk-theme  
但是感觉和deepin的桌面环境搭不起来，有些效果会无效。【待研究】
<p>&nbsp;</p><p>&nbsp;</p>
### 移动launcher中图标分类示例
使用文本编辑器改变/usr/share/applications/中对应desktop文件的Categories后面的值  
如果上面改了值分类还是没有改变，emm，似乎deepin有点问题，我们还要把这个desktop文件名字稍微改一下：  
sudo mv /usr/share/applications/edrawmax-zh.desktop /usr/share/applications/edrawmax.desktop


## 重要应用（我觉得）
### docker
https://github.com/ExplosiveBattery/docker  
仓库中有两个pdf，一个是介绍docker，一个是如何安装docker，我的deepin安装使用了：  
`wget -qO- https://get.docker.com/ | sh` 一条命令解决  
`cat /etc/debian_version` 可以看到deepin15.5是debian 8.0 sid（也就是jessie unstable）  
### katoolin
https://github.com/LionSec/katoolin  
自己选择部分工具安装即可，不推荐使用kali docker，因为docker不适合会变动的东西，比如部分经常有更新的软件：metasploit，nmap  
