# 参考文章
https://www.himiku.com/archives/homepage.html

本章将上面文章进行修改，使更多人能更容易理解

# 效果图

<img src=/image/hp1.png width="100%" height="100%">

<img src=/image/hp2.png width="100%" height="100%">

# docker-comepose.yml
       version: "3.3"
       services:
         homepage:
           image: ghcr.io/gethomepage/homepage:latest
           container_name: homepage
           ports:
             - 内网端口:容器端口
           volumes:
             - 在本机的安装目录(绝对路径):/app/config 
             - 外置硬盘在本机的挂载目录:随便起，带/不带中文，如"/123"
             - /var/run/docker.sock:/var/run/docker.sock 
           environment:
             PUID: $PUID
             PGID: $PGID

附: linux挂载SMB硬盘

!> ip为内网环境下
> /etc/fstab内修改

       mount -t cifs //目标主机ip/共享文件夹名 本机文件夹绝对路径 -o username=对应SMB用户,password=密码 0 0

# bookmarks

默认界面下"DEV"项

觉得好看就改URL

不好看就全删掉

# services

例子，顶格写，保存后刷新homepage页面生效

       - 工具:
           - tp官网:
               href: https://www.tp-link.com.cn
               icon: https://www.tp-link.com.cn/favicon.ico
               description: tplink

# widgets

homepage顶部配置

例子(顶格):

       - resources:
           label: 本机系统信息
           cpu: true
           memory: true

       - resources:  
           label: 本机硬盘 
           disk: /

       - resources:
           label: 硬盘2
           disk: 挂载硬盘在容器内的目录名

       - datetime:
           text_size: xl
           format:
             timeStyle: short
             hour12: true

       - search:
           provider: bing
           target: _blank

       - openmeteo:    
           label: 屯昌县 # 百度当地坐标    
           latitude: 19.8   # 当地纬度
           longitude: 109.45 # 当地经度
           timezone: Asia/Shanghai    # 时间，不会就别改
           units: metric     
           cache: 5 

# setting

例子:

     language: zh-CN
     hideVersion: true
     title: Homepage面板✨
     favicon: https://s21.ax1x.com/2024/07/12/pk4Vjdf.jpg
     background:
       image: https://s21.ax1x.com/2024/07/28/pkqIL1f.png
       saturate: 100 #饱和度，范围 0, 50, 100... 参考 https://tailwindcss.com/docs/backdrop-saturate
       brightness: 75 #亮度，范围 0, 50, 75... 参考 https://tailwindcss.com/docs/backdrop-brightness
       opacity: 100 #不透明度，范围 0-100
