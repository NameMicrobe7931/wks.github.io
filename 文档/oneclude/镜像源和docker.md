# 更新镜像源

使用powershell/cmd连接到玩客云SSH后台，命令格式为：

           ssh root@内网IP

如果指定端口号，则在内网IP后空一格，加上     

           -p 修改后端口

回车，输入yes接受密钥后回车，输入密码后回车进入SSH后台

镜像源下载地址：https://baipiaopan.118pan.com/b1150424 密码lll4
删除/etc/apt内的"soueces.list"和/etc/apt/sources.list.d内的"armbian.list"两个文件
将下载好的文件复制一份，一份命名为"sources.list",一份命名为"armbian.list"
然后将命名好的"armbian.list"和"sources.list"分别放回两个文件夹

或者使用sudo nano编辑两个文件，将下载好的文件打开，粘贴里面的内容到armbian.list和sources.list并保存

使用sudo apt update和sudo apt upgrade更新

# docker安装

更新镜像源，使用以下命令安装docker前置
 
          sudo apt-get install docker.io
        
安装完成后即可用 "docker pill" 加镜像名拉取镜像

> 注意

2024年6月份开始，国内开始下架docker国内仓库站点，会导致拉取超时，因此需要配置镜像加速地址

# docker加速地址

部分docker加速地址，建议全都用上，部分地区可能用了还是超时
          
          https://docker.1panel.live
          https://ghcr.nju.edu.cn
          https://ghcr.m.daocloud.io
          https://registry-k8s-io.mirrors.sjtug.sjtu.edu.cn
          https://k8s.m.daocloud.io
          https://k8s.nju.edu.cn
          https://gcr.nju.edu.cn
          https://k8s-gcr-io.mirrors.sjtug.sjtu.edu.cn
          https://k8s-gcr.m.daocloud.io
          https://quay.nju.edu.cn
          https://quay.m.daocloud.io
          https://hub-mirror.c.163.com
          https://docker.m.daocloud.io
          https://docker.mirrors.ustc.edu.cn
          https://reg-mirror.qiniu.com
          https://docker.nju.edu.cn
          https://docker.mirrors.sjtug.sjtu.edu.cn
          https://quay.mirrors.ustc.edu.cn
          https://nvcr.nju.edu.cn
          https://nvcr.m.daocloud.io
          https://hub-mirror.c.163.com
          https://mirror.baidubce.com
          https://dockerproxy.com
          https://mirror.baidubce.com
          https://docker.nju.edu.cn
          https://docker.mirrors.ustc.edu.cn
          https://docker.m.daocloud.io
          https://ccr.ccs.tencentyun.com
          https://dockerhub.azk8s.cn   