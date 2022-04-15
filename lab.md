# linux工具

## linux常用命令

//连接服务器

`ssh name@ip`

//后台执行程序

`nohup python3 -u run.py > log 2>&1 &`

//实时查看程序输出

`tail -f log`

//其他常用命令

`history grep cat ps kill pkill tail head top df echo awk sed cut paste ls ll mk rm等等`

## nvidia-docker

//Docker仓库中搜索镜像

`nvidia-docker search imagename`

//获取镜像

`nvidia-docker pull imagename`

//创建指定镜像上的容器，并进入容器

`nvidia-docker run -it -v /Users/liusuldier/data:/root/data --name mycontainer imagename /bin/bash`

//退出容器

`exit`

//启动容器

`nvidia-docker start containerID`

//进入容器

`nvidia-docker exec -it mycontainer /bin/bash`

//查看镜像

`nvidia-docker image ls (-a)`

`nvidia-docker images`


//删除镜像

`nvidia-docker rmi imageId`

//查看容器

`nvidia-docker ps (-a)`

//删除容器

`nvidia-docker rm containerID`

//容器保存为镜像

`nvidia-docker commit containerID imagename:imagetag`

//上传镜像到docker仓库

`nvidia-docker login`

`nvidia-docker push imagename:imagetag`


//部署

`apt-get install -y docker`

`systemctl start docker`

`docker --version`

`docker pull imagename:imagetag`


// Dockerfile

`FROM imagename:imagetag`

`RUN mkdir a`

// 编译Dockerfile

`docker build -t newimage:tag .`

`docker run -it myubuntu:2 /bin/bash`

// 本地访问服务器端docker中的tensorboard

1 本地登陆服务器，-L为端口映射

`ssh -L 6006:127.0.0.1:6006 -p 60059 liushujun@120.25.121.173`

2 服务器端操作如下

`nvidia-docker run -it -p 6006:6006 --name shujunliu_test -v /home/liushujun/data:/root/data shujun/tensorflow-tts:v2 /bin/bash`

`tensorboard --logdir=examples/tacotron2/exp/train.tacotron2.v1/ --bind_all`

// 本地访问服务器端docker中的jupyter

`ssh -L 8888:127.0.0.1:8888 -p 60059 liushujun@120.25.121.173`

`nvidia-docker run -it -p 8888:8888 --name shujunliu_test -v /home/liushujun/data:/root/data shujun/tensorflow-tts:v2 /bin/bash`

`jupyter notebook --ip='*' --port=8888 --no-browser --allow-root`

## github 

//本地创建项目并推送到gihub

`mkdir project && cd project`

`git init`

`git add --all . `

`git commit -m "first commit"`

`git remote add origin https://liushujun@192.168.0.201/liushujun/TSM_PSM.git`

`git push -u origin master`

//从github获取代码

`git clone url`

`git pull`

## vim常用命令

`i 插入`

`dd 删除一行`

`yy 复制一行`

`pp 粘贴一行`

`/a 查找a`

`%s/a/b/g a替换为b`

`gg 跳转到页首`

`GG 跳转到页尾`

`^ 跳转到行首`

`$ 跳转到行尾`

`wq 保存并退出`

`q！ 强制退出`



