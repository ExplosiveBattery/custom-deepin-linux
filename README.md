## 基本操作
### 直接root权限登录系统
两种思路：
- 将默认的登录用户永久提升到root权限
- 调整Lightdm（配置文件/etc/lightdm/lightdm.conf，相关帮助https://www.cnblogs.com/EasonJim/p/7128317.html）  

重要提示：https://www.cnblogs.com/johnw/p/5499442.html 中的方法三直接将uid改为0，是一个坑。会导致开机无法登录。因为lightdm有限制，我将uid改为1001，能够显示登录界面但是登录不进去，估计home目录里面也有限制要调整。
### bug修复
https://blog.csdn.net/liuestcjun/article/details/53515589 15.5.1还存在这个bug，导致我不能使用java命令运行class文件  
为英语环境下的日历添加农历支持:https://bbs.deepin.org/forum.php?mod=viewthread&tid=154593&extra=page%3D1&page=2
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
如果想要编译安装最新版的dock可以参考https://bbs.deepin.org/forum.php?mod=viewthread&tid=155729 关键是注意还要更新dtkcore
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
### 移动launcher中图标分类示例
使用文本编辑器改变/usr/share/applications/中对应desktop文件的Categories后面的值  
如果安装的是win下应用，那么在/usr/local/share/applications，比如通过商店安装的百度云，迅雷
如果上面改了值分类还是没有改变，emm，似乎deepin有点问题，我们还要把这个desktop文件名字稍微改一下：  
sudo mv /usr/share/applications/edrawmax-zh.desktop /usr/share/applications/edrawmax.desktop
### 精简系统
可以删除系统多余的语言包，有几百MB大小
### 解决wireshark（dumpcap）的权限问题
sudo chmod 4755 /usr/bin/dumpcap
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

...不少人向我推荐VS code...
