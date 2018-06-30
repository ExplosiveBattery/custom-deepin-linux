### linux的开机启动管理从initd逐渐换成了systemd
所以你可以发现一些常用命令已经被取代：    
![picture](https://github.com/ExplosiveBattery/custom-deepin-linux/blob/master/autostart/DeepinScreenshot_select-area_20180503083915.png?raw=true)


### 开机自执行有这么几种形式
1. 创建一个服务，然后systemctl enable一下，比如说nginx，apache这种服务器
2. 添加执行命令到rc.local，比如你想要在开机的时候默认关闭蓝牙省电：rfkill block bluetooth
3. 添加desktop文件到~/.config/autostart或者/etc/xdg/autostart/。deepin在launcher中右键的“add to startup”会添加到~/.config/autostart，所以效果会只限于你这个用户，其他用户登录没有效果。如果要弄成全局的，就要放到/etc/xdg/autostart/，如果你安装了blueman，它的开机自启动就在这里。

![picture](https://github.com/ExplosiveBattery/custom-deepin-linux/blob/master/autostart/DeepinScreenshot_select-area_20180503085258.png?raw=true)  
注意：似乎如果有设计UI内容的东西，只有3会成功，比如开机自动启动conky

```shell
桌面壁纸自动切换，600是秒数，也就是开机后每隔10分钟自动换
vega@vega-Laptop:~$ cat /etc/xdg/autostart/change-desktop-background.desktop 
[Desktop Entry]
Type=Application
Name=Change desktop background
Exec=/usr/share/backgrounds/change_desktop_background.sh 600&
NoDisplay=true

vega@vega-Laptop:~$ cat /usr/share/backgrounds/change_desktop_background.sh
#!/bin/bash
PATH=/media/vega/0D6C051A0D6C051A/all/Wallpapers/*
if [ $1 -ne 0 ]; then
	# 随机文件版
	while [ 1 -eq 1 ]; do
	    list=$(/bin/echo $PATH)
	    num=$(/bin/echo $list | /usr/bin/wc -w)
	    filepath=$(/bin/echo $list | /usr/bin/awk "{print \$$[$RANDOM%num]}")
	    #/usr/bin/gsettings set com.deepin.wrap.gnome.desktop.background picture-uri file://$filepath
	    /usr/bin/qdbus --literal com.deepin.wm /com/deepin/wm com.deepin.wm.ChangeCurrentWorkspaceBackground file://$filepath > /dev/null
	    /bin/sleep $1;
	done

	# 固定循环版
	# while [ 1 -eq 1 ]; do
	#     for i in $(echo $PATH/*); do
	#         echo $i
	#         gsettings set com.deepin.wrap.gnome.desktop.background picture-uri file://${i}
	#         sleep $[10*60];
	#     done
	# done
fi




conky自启动
vega@vega-Laptop:~$ cat /etc/xdg/autostart/conky.desktop 
[Desktop Entry]
Type=Application
Name=Conky
Comment=Start conky script
Exec=conky -d
```








