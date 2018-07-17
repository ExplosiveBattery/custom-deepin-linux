No license， just for fun  

deepin is convenient, but lost something.

## 基本操作
### FAQ（常见问题）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=146921  
### 更换软件源，处理问题源
sudo gedit /etc/apt/sources.list   
deb http://mirrors.aliyun.com/deepin panda main contrib non-free   
deb-src http://mirrors.aliyun.com/deepin panda main contrib non-free   
sudo rm /etc/apt/sources.list.d/spotify.list  
### 替换apt：  
apt-fast是用来代替“apt-get”的的一个shell脚本程序，它通过多线程的方式改善了更新和下载安装包的速度。如果你经常用终端和apt-get来安装和升级软件的话，可以试试apt-fast  
sudo add-apt-repository ppa:apt-fast/stable  
sudo apt update  
sudo apt install apt-fast  
### 软件源支持add-apt-repository ppa
sudo apt install software-properties-common  
apt安装java、katoolin时会用到 
### 直接root权限登录系统
两种思路：
- 将默认的登录用户永久提升到root权限
- 调整Lightdm（配置文件/etc/lightdm/lightdm.conf，相关帮助https://www.cnblogs.com/EasonJim/p/7128317.html）  

重要提示：https://www.cnblogs.com/johnw/p/5499442.html 中的方法三直接将uid改为0，是一个坑。会导致开机无法登录。因为lightdm有限制，我将uid改为1001，能够显示登录界面但是登录不进去，估计home目录里面也有限制要调整。
### 不能做的事情
ln -f /usr/bin/python3 /usr/bin/python  因为一些东西依赖于python，且他们认为系统的python是指python2，所以不要做这个改动  
不要随意删除/usr/share/applications下的desktop，不要以为这只是一个为了在launcher中显示的文件。比如你删了File manager，你会发现系统设置中对应的Super+E快捷键失效；你删了Text Editor你会发现文本文件右键打开方式出了点问题；删除了deepin-font-install之后，就不能直接通过双击安装软件。当然也有一些真的放着碍眼，你就删掉吧，如果要回复，使用apt install --reinstall  xxxx    
### bug修复
https://blog.csdn.net/liuestcjun/article/details/53515589 15.5.1还存在这个bug，导致我不能使用java命令运行class文件  
为英语环境下的日历添加农历支持:https://bbs.deepin.org/forum.php?mod=viewthread&tid=154593&extra=page%3D1&page=2
### 引导修复
见Repair grub文件夹（信不信？不管你遇到过的还是没遇到过得）
### apt remove/purge 手贱 修复
cat /var/log/apt/history.log 查看操作历史
### 内核定制（好处，教程）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=155660&extra=  
一般步骤：http://smilejay.com/2011/05/linux_kernel_compilation/  
### 开机动画
见plymouth文件夹  
### 切换桌面壁纸（脚本，内存泄露问题）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=155474&extra=  
### 动态桌面壁纸
有待我开发【待研究】
### 桌面美化(conky，类似于windows下的水滴桌面)
见conky文件夹  
### 设置开机自动执行什么(包含开机应用自启动，比如说conky，壁纸自动切换)
见autostart文件夹
### 配合conky的show desktop
https://github.com/ExplosiveBattery/deepin-desktop-toggle  
程序会读取~/.toggleconfig中的每一行作为一个顶级窗口名，如果存在同样的窗口名则不会被ShowDesktop（win+d按键）影响
### 钉宫语音包
https://bbs.deepin.org/forum.php?mod=viewthread&tid=154264  这个帖子楼主的包有点不完善，拉到后面有人发了比较好的  
类似的还有https://bbs.deepin.org/forum.php?mod=viewthread&tid=134778
### launcher
想要给launcher自定义分类
https://github.com/linuxdeepin/dde-launcher/search?utf8=%E2%9C%93&q=chat&type= 从代码看出是写死的，而不是读取配置文件，很遗憾这种写法，如果要实现自定义分类就需要重新编译这个项目  
### topbar(顶栏)
https://bbs.deepin.org/forum.php?mod=viewthread&tid=141816
### 透明化dock(底栏)
https://bbs.deepin.org/forum.php?mod=viewthread&tid=149493  
自定义dock大小：
https://jingyan.baidu.com/article/f7ff0bfc3f49132e26bb1338.html （还可以使用gsettings命令）  
如果想要编译安装最新版的dock可以参考https://bbs.deepin.org/forum.php?mod=viewthread&tid=155729 关键是注意还要更新dtkcore
### 天气Dock插件
https://bbs.deepin.org/forum.php?mod=viewthread&tid=156934
### 应用图标定制
见icons文件夹
### 无线网卡工作模式
`iwconfig`  
如果发现有一行Power Management:powersave说明网卡工作在低功耗，emmm，我觉得这可能是我信号不好的原因  
`sudo iw dev wlp2s0 set power_save off`  
### 省电
tlp、linux-cpupower 没准安装了之后是一种省电方式  
但是我也觉得不太好，官方说15.6版本会对这方面进行解决优化  
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
### 提高音质
https://bbs.deepin.org/forum.php?mod=viewthread&tid=137002
### 主题
目前为止好看的主题：  
https://github.com/horst3180/Arc-theme  
https://bbs.deepin.org/forum.php?mod=viewthread&tid=166024  
https://github.com/adapta-project/adapta-gtk-theme  
https://bbs.deepin.org/forum.php?mod=viewthread&tid=159620  
但是感觉和deepin的桌面环境搭不起来，有些效果会无效。【待研究】
### 替换最大化最小化按钮（仿mac）
https://bbs.deepin.org/forum.php?mod=viewthread&tid=156341
### 移动launcher中图标分类示例
使用文本编辑器改变/usr/share/applications/中对应desktop文件的Categories后面的值  
如果安装的是win下应用，那么在/usr/local/share/applications，比如通过商店安装的百度云，迅雷
如果上面改了值分类还是没有改变，emm，似乎deepin有点问题，我们还要把这个desktop文件名字稍微改一下：  
sudo mv /usr/share/applications/edrawmax-zh.desktop /usr/share/applications/edrawmax.desktop
### 精简系统
可以删除系统多余的语言包，有几百MB大小  
`
sudo apt purge spotify-client steam skype thunderbird dde-introduction deepin-manual deepin-clone simple-scan  
`  
`
sudo rm /usr/share/applications/skype.desktop /usr/share/applications/dde-trash.desktop  /usr/share/applications/deepin-toggle-desktop.desktop /usr/share/applications/org.gnome.FileRoller.desktop /usr/share/applications/dde-computer.desktop /usr/share/applications/deepin-feedback.desktop  
`  
` 我不支持deepin的flatpak，删了之后自己进应用市场搜deepin，去安装deb格式  
flatpak uninstall org.deepin.flatdeb.deepin-calculator org.deepin.flatdeb.deepin-calendar org.deepin.flatdeb.deepin-image-viewer org.deepin.flatdeb.deepin-music org.deepin.flatdeb.deepin-screen-recorder org.deepin.flatdeb.deepin-screenshot org.deepin.flatdeb.deepin-voice-recorder org.deepin.flatdeb.Base.Platform  
`  
### 解决wireshark（dumpcap）的权限问题
sudo chmod 4755 /usr/bin/dumpcap

<p>&nbsp;</p><p>&nbsp;</p>


## 重要应用（我觉得）
### Java
apt安装：https://www.cnblogs.com/diyunfei/p/7618508.html  
压缩包安装（推荐）：https://bbs.deepin.org/forum.php?mod=viewthread&tid=136610  
### gradle
压缩包安装： https://gradle.org/install/   
如果有Android Studio，可以通过这个IDE下载安装  
不推荐通过apt install 安装  
### docker
https://github.com/ExplosiveBattery/docker  
仓库中有两个pdf，一个是介绍docker，一个是如何安装docker，我的deepin安装使用了：  
`wget -qO- https://get.docker.com/ | sh` 一条命令解决  
`cat /etc/debian_version` 可以看到deepin15.5是debian 8.0 sid（也就是jessie unstable）  
### katoolin
https://github.com/LionSec/katoolin  
自己选择部分工具安装即可，不推荐使用kali docker，因为docker不适合会变动的东西，比如部分经常有更新的软件：metasploit，nmap  
### QT Creator
应用商店的软件常常版本落后，就需要我们自己去安装：  
`sudo apt-get install libgl1-mesa-dev build-essential`(见http://doc.qt.io/qt-5/linux.html 虽然不是编译安装，但是我发现还是需要libgl1-mesa-dev)   
接着安装指导：https://www.jianshu.com/p/afbc42ad2cfd  
下载页面：http://download.qt.io/archive/qt/  
最后记得编辑/etc/profile(或者~/.bashrc)，来实现每一次开机自动export Qt安装目录中的bin文件。或者自己一个个ln -s到/usr/bin目录中
- 注意：
- 选择安装的时候，QT Creator和Qt下的desktop gcc是必选的，后者会为你提供qmake等工具
- qmake: could not exec ‘/usr/lib/x86_64-linux-gnu/qt4/bin/qmake’: No such file or directory  
 https://blog.csdn.net/zhuquan945/article/details/52818786 </b>
### 思维导图
Edraw MindMaster，XMIND，mindmaps网页版，百度脑图网页版
### 流程图等
Edraw Max（相当于windows visio）（Edraw支持多方跨平台，值的付费）
### Office
LibreOffice 不少人推荐，但是我习惯操作界面类似于Word的WPS 
https://uzer.me 网页版，需要网络良好时使用  
### 文件比较
Beyond Compare，VS code内置插件，Meid
### 数据库连接工具
datagrip，Navicat，dbeaver
### 笔记
为知笔记，有道云笔记，映像笔记
### Markdown
Cmd Markdown（导出pdf需要购买会员），Typora，VS code内置插件
### 邮箱客户端
Foxmail（wine模拟，耗电，所以如果脱离电源不要开着）
### 阅读器
Comix 漫画阅读器  
追书神器安卓版  
福昕阅读器Foxit Reader  
### 计算机网络学习
Cisco Packet Tracer，GNS3
### 输入法
搜狗，Rime
### 写作/Markdown
https://ivarptr.github.io/yu-writer.site/index.html  
### 系统临时状态
专门用于使用真机进行自己内心不想进行的操作  
通过shell命令进入系统临时状态，并且记录其间shell的交互情况  【难度巨大，等待完成】
### BT系列
迅雷  
webtorrent BT视频  
### 驱动
Driver Manager  
### 分区
Gparted 这款软件还可以单独写到PE里面  
### 清理垃圾?
deepin repair 一般一键备份前用一下，减少备份包体积
### 系统配置文件更改
dconf editor  比如改桌面的各种配置，都可以在这通过UI操作  
### 字体查看
font viewer  
### VMware pro 14.1.2
https://download.pchome.net/system/sysenhance/download-75584.html  
密钥：http://beikeit.com/post-513.html  的 “最新14版”  
### 下载youToBe、bilibili等视频
请自己安装好pip3  
pip3 install  you-get  
但是有一个问题，pip3安装的you-get、scrapy等脚本程序都放到了~/.local/bin下，而这里还需要我们自己加到$PATH里面  

## 常用快捷键

<b>能用常用快捷键打开的东西，就可以不必放在dock中</b>  
Shift+Win+左右方向键 在多任务视图中移动当前应用  
Win+方向上键 当前窗口最大化    
Win+方向下键 当前窗口正常化  
Win+= 与 Win+- 放大镜效果  
Win+e 文件管理器  
Win+w 当前任务视图中的所有窗口  
Ctrl+Alt+T 终端shell  
