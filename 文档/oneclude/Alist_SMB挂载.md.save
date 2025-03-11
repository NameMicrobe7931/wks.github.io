# Alist-SMB挂载

# 前言

<img src=/image/alist.png width="100%" height="100%">

因为Alist的官网文档内没有完整的SMB挂载方式（而且之前提交过一次文档到github，然后因为当时逆天的网络环境，不知道有没有成功）

还有之前被这玩意折磨到崩，为了这玩意的教程能更快的被更多人看到，直接搓了这么个玩意

> 要是隔了几个月还没上的话麻烦哪个大哥帮我把这章全部拷贝上去，记得开头标记“教程来自：IKWIKI”

# SMB安装和挂载测试

      docker image：iknbds.top:5300/dperson/samba:latest

这个是本站的镜像源，哪天拉不动了就是镜像站暴毙了

暴毙了就看本站镜像源和docker那章自个加上加速地址

下边是docker启动命令，第一个端口没试出来是干什么用的，第二个是SMB的共享端口，最好默认445

      docker run -it --name 给容器起的名字 -p 局域网端口: -p 445:445 -v Linux主机内文件夹的绝对路径:/mount -d 镜像名 -u "用户名;密码" -s "共享文件夹根目录;/mount/;yes;yes;yes;all;none"

例如:

      docker run -it --name samba -p 80:80 -p 445:445 -v /./media/video:/mount -d dperson/samba -u "admin;adminadmin" -s "test;/mount/;yes;yes;yes;all;none"

smb主机ip为：192.168.10.10，两个端口已放行
win+r打开运行框，输入：

      \\192.168.10.10

回车，文件管理器自动打开目标主机的共享文件夹，显示的文件夹名为“test”,图标是一个普通的文件夹图标，图标下方加上一个绿白色的管道之类的标，打开后可以看到位于  /./media/video   内存放的文件

# Alist挂载Linux主机目录

打开Alist的管理-存储界面，新添加一个SMB驱动

挂载路径:挂载文件夹显示在主页的名称，随便起

地址是SMB主机的局域网IP，默认445，账号密码在刚刚运行的docker run命令内

根文件夹路径不变

!> 注意！ 分享名称一定一定一定要填写共享文件夹的根目录名

根目录名就像这样

<img src=/image/smb.png width="100%" height="100%">

不然就会出现：

Failed init storage: mount \\192.168.10.10: mount path must be a valid share name (\\<server>\<share>)

保存后会立即生效

(一般情况下，同一台linux物理机开了docker alist和docker smb是挂载不了的)

(应该没人会闲的蛋疼这么玩吧)

# Alist挂载Windows共享文件夹

按理来说应该是Windows挂载linux主机的共享文件夹+开专属网络驱动器位置，就像b站那些玩nas的一样文件管理器内一堆局域网硬盘

但是以防万一，还是加上这一项

Windows右键文件夹-属性-共享内开放文件夹共享

任务栏自带的搜索图标内搜索“高级安全 Windows Defender 防火墙”

出入站规则均放行TCP445端口

为了更好的体验(人话就是防止暴毙)，建议电脑获取IP方式改为静态上网，至于怎么填写初高中信息课或者百度有教程

用户名就是共享文件夹时电脑登录的那个本地用户名

密码是电脑屏幕解锁密码

右键开启共享的文件夹，分享名称就是电脑共享文件夹上显示的网络路径，全选粘贴即可

> 演示地址:

http://iknbds.top:10180/

账号密码都是admin

(alist不要学我一样往头文件栏内硬塞音乐外链，抽象的很)
