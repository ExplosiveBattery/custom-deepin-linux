# 开机自启动
开机启动有这么几种形式：
1. 创建一个服务，比如说nginx，apache这种服务器
2. 添加执行命令到rc.local，比如你想要在开机的时候默认关闭蓝牙省电
3. 添加desktop文件到~/.config/autostart或者/etc/xdg/autostart/。deepin在launcher中右键的“add to startup”会添加到~/.config/autostart，所以效果会只限于你这个用户，其他用户登录没有效果。如果要弄成全局的，就要放到/etc/xdg/autostart/。
