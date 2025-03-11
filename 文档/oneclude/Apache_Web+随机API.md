# Apache2+PHP实现随机图片API

> 参考博客是腾讯云的某个大佬写的，找不到了

# 前言
因为宣传博客的背景太单一了，外边的随机图片不好看

(其实是想要对学生发电)(bushi

# 图床部署

本站内有

# Apache2安装

      apt update
      apt upgrade
      apt-get install apache2

ufw/firewall放80端口后输入127.0.01或者局域网IP即可看到apache生成的欢迎界面

# PHP安装、apache2开启php支持

      apt install php8.2

安装成功后在/var/www/html内新建一个php文件，文件内填入

      <?php 
      phpinfo( ); 
      ?>
      
保存并退出

然后在ip后边加上  /php文件名.php   ，出现php信息后证明php安装成功

apache2的配置文件在   /etc/apache2  内，其中  sites-available  文件夹为虚拟主机配置文件夹

使用nano打开apache2.conf

    nano -l /etc/apache2/apache2.conf

在第175行粘贴这段命令

    175
    176 <Directory /var/www/html>
    177         Options Indexes FollowSymLinks
    178         AllowOverride All
    179         Require all granted
    180 </Directory>

> 数字作为定位使用，粘贴后要删掉数字,不删会炸的

保存并退出，使用  
 
    systemctl restart apache2
    systemctl status  apache2

验证重启成功

# PHP文件配置

回到/var/www/html,使用rm *删掉所有文件，新建一个文件夹

进入文件夹后使用nano/vim创建一个index.php和一个txt文本

php内容:

    <?php
    $arr=file('txt文件名.txt');
    $n=count($arr)-1;
    for ($i=1;$i<=1;$i++){
    $x=rand(0,$n);header("Location:".$arr[$x],"\n");}
    ?> 

TXT内粘贴图片直链

> 例如：https://s21.ax1x.com/2024/07/28/pkqIL1f.png

保存并退出

输入http://局域网IP或127.0.0.1/文件夹名即可生成图片

# 野路子

在刚刚的操作中，我们把/var/www/html内的文件统统删掉了

如果我们再次打开http://局域网IP或127.0.0.1，就会发现

<img src=/image/12.png width="100%" height="100%">

再往里边丢个图片

<img src=/image/1-32.png width="100%" height="100%">

打开图片，仔细看看URL,格式是不是有些眼熟

本质上来说，图床的原理是通过upload.php上传图片到图床服务端的images文件夹里，重命名后按照时间顺序储存

而我们把/var/www/html内的index.html替换成图片后在网页内打开并复制URL的操作

和图床工作原理是一样的

只不过这些步骤由图床服务端完成了

因此，在php所在目录内新建一个文件夹，文件夹内存放图片，再把外网路径放到txt文件内即可

# 方法

> 文档以/var/www/html为apache工作目录，/var/www/html/batca为随机图片根目录,12.tpddns.cn为网站域名

批量重命名
    
    cd /var/www/html/batca/tp    #cd到图片文件夹内
    
    i=1; for file in *; do mv "$file" "$((i++)).${file##*.}"; done

输出文件路径到txt内

    find /var/www/html/batca/tp -type f -exec readlink -f {} \; > /var/www/html/batca/iu.txt

修改成外网路径

    sed -i 's|/var/www/html/batca/tp|http://12.tpddns.cn/batca/tp|g' /var/www/html/batca/iu.txt

最后在/var/www/html/batca内放入php文件，指定php文件调用的txt文件名

打开http://12.tpddns.cn/batca即可正常访问

imgsrc调用
    
    <img src="api地址" class="imgs"/>

# 注意事项

https网页调用api时，需要为api地址单独做一套带https的二级地址

使用http://根域名作为api地址时网页会默认使用https头导致图床超时