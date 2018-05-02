### software
	Plymouth：深度操作系统所使用的开机动画程序。  
	Bootsplash:第一款开机动画程序，目前已经被Splashy取代。  
	fbsplash:为了取代bootsplash，Gentoo开发的新开机动画程序。     
	Splashy:新的开机动画程序，以取代老化的bootsplash开机动画程序。  
	usplash:ubuntu之前早期使用的开机动画程序。  
	XSplash:Ubuntu9.10开始使用的开机动画程序。  
### config file for plymonth  in deepin
  如果你只改动/etc/plymouth/plymouthd.conf 则只有对关机动画起作用  
  还需要改动/usr/share/plymouth/themes/default.plymouth 开机动画  
  deepin提供了plymouth-set-default-theme 但是只改了/etc/plymouth/plymouthd.conf  
  最后sudo update-initramfs -u 刷新

### theme download
https://store.kde.org/browse/cat/108/  
recommend：  
https://store.kde.org/p/1200272/  
https://store.kde.org/p/1200274/  
