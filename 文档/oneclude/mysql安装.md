# 简介

在以往的认知中，我们都会认为Mysql这玩意只能给x86、server这种东西来玩

但是这玩意也可以给安到玩客云上并且正常使用

而且占用不高

<img src=/image/02.png width="100%" height="100%">

# 安装方法

本教程使用的是1penal，其他面板同理

配置好加速地址后，使用docker pull拉取biarms/mysql:5.7.30

应用商店内搜索mysql后点击安装，在安装信息填写那一页拉到最底下，点击“编辑compose文件”

找到“image”项目后，删去后面的镜像，粘贴上刚刚下载好的biarms/mysql:5.7.30，设置好其他参数后点击安装

或者终端内使用这条命令

            docker run -p 端口:端口 --name docker的名称 -e MYSQL_ROOT_PASSWORD=MySQL的root密码 -d biarms/mysql:5.7.30

替换掉中文注释为实际参数

运行后转到面板，将mysql停止运行，修改网络形式为“host”后点击确定重新运行

> 这段改网络类型是为了让其他docker和主机能正常连接到mysql

重新运行后点击数据库-远程服务器内添加远程服务器

名称任意，版本选5.7x，数据库地址填玩客云的静态ip，端口和密码修改完成后点击连接测试和确认来添加mysql

至此，mysql已经成功运行在玩客云上