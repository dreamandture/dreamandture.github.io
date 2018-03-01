---
title: docker 使用
date: 2018-03-01 11:54:59
categories: develop
tags:
   - operation
---
docker 安装与使用
<!-- more-->

##1.运行一个

```
    sudo docker run -t -i ubuntu:14.04 /bin/bash
    docker start eafd9111ada6                # 启动容器
```

##1.镜像保存

    docker commit -a 'message aaaa' CONTAINER_ID NEW_IMAGE_NAME 
    #把该容器保存为一个新镜像
    docker commit -m='hello_world' -a="lance" 3eec6a474897 hello_world/lance
##2.删除
```
     docker rmi IMAGE ID 删除
     docker rmi -f IMAGE ID 强制删除
     docker rm $(docker ps -a -q) #删除所有已经停止的容器
```


##3.导入导出

     docker save -o ubuntu_14.04.tar ubuntu:14.04 ＃导出的是镜像
      #导入：
     sudo docker load < ubuntu_14.04.tar 
     #或者
     docker export <CONTAINER ID > > my_container.tar  #导出的是容器不是镜像
     cat my_container.tar |docker import - image_name:tag  
    

##4.进入容器

```
docker exec -it eafd9111ada6  /bin/bash  # 进入容器
```

```
docker history image_id


```





#问题记录
##1. docker命令自动补全功能
最小化安装centos后发现git docker等命令不能自动补全参数,而在Desktop安装环境下是可以自动补全的.

    yum install bash-completion -y
##2.修改启动路径
###2.1 Centos6下
/etc/sysconfig/docker里面加入

    other_args="-g /data/docker"
###2.2 Centos7下
修改
    vim /usr/lib/systemd/system/docker.servicervice为
    ExecStart=/usr/bin/docker daemon -H fd:// --graph /data/docker 
##3.docker-runc did not terminate sucessfully: unknown
```sh
yum install http://mirror.centos.org/centos/7/os/x86_64/Packages/libseccomp-2.3.1-3.el7.x86_64.rpm

```