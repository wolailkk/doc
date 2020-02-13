步骤图文参考目录:
https://support.apple.com/zh-cn/HT208969
https://support.apple.com/zh-cn/HT201372
https://support.apple.com/zh-cn/HT208496


1.下载安装程序
下面是这个步骤解决方法的链接和步骤
说明:技术支持页面搜索   HT208969
https://support.apple.com/zh-cn/HT208969
翻滚到第四项目
下载 macOS High Sierra
点击
升级到 macOS Catalina
打开appstore
说明（如果提示版本过低不要紧，他是与你当前系统发生的警告）

2.磁盘


打开系统内的磁盘工具，点击，抹掉
确保这个驱动器至少有 12GB 可用储存空间，并已格式化为“Mac OS 扩展”。
名字命名为      MyVolume
步骤1下载完毕后，在应用程序会出现    “安装 macOS High Sierra”
打开终端
输入:
sudo /Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
中间会提示密码和询问，密码为当前开机密码，询问输入y
之后就交给程序进行安装配置，当回复 "Done"结束，推出u盘，插入到重装电脑
下面是这个步骤解决方法的链接
说明:技术支持页面搜索    HT201372
https://support.apple.com/zh-cn/HT201372


3.下面步骤如果需要密码，就是系统之前的开机密码
按住Option开机  显示磁盘选择，选择u盘
点击磁盘管理工具
抹掉hd下面的所有小磁盘
再点击刚刚抹掉的盘  在综卷下点击  ”-“ 号，那俩都删除掉，然后选择hd
选择抹掉，名称无所谓，格式一定要是APFS
好了后退出访达，点击重新安装系统，就ok了！
下面是这个步骤解决方法的链接
https://support.apple.com/zh-cn/HT208496
