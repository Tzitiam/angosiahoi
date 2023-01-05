## window 中使用dockers</br>

### 开启和关闭docker服务
- 开启服务：
    Net start com.docker.service
- 关闭服务：
    Net stop com.docker.service

### 一、镜像命令
#### 1.显示本地主机上所有镜像<br>
- docker images [可选项]
    - 可选项：<br>
    **-a**  列出所有镜像<br>
    **-q**  只显示镜像id
#### 2.搜索镜像<br>
- docker search 镜像名

#### 3.下载镜像<br>

- docker pull **镜像名**
     = docker pull **docker.io//ibrary/mysql:latest** (默认最后一个版本)

    - 注：如果需要指定版本用<br>
        docker pull 镜像名：tag（版本号）
    <br>例如：docker pull mysql:5.7       
    - 不写版本号会默认下载最后一个版本（latest)。

#### 4.删除镜像(可用镜像名，也可用镜像id）<br>
- docker rmi -f **镜像id**
    - 删除多个镜像<br>
    docker rmi -f **镜像id** **镜像id** **镜像id**
    - 还有直接清空所有镜像的命令，暂时没用到

### 二、容器命令（有镜像才能创建容器）

#### 1.新建容器并启动<br>
- docker run [可选参数] image

    - 参数说明：<br>
        - --name="name"  设置容器名字<br>
        - -d 后台方式运行<br>
        - -it 使用交互式运行<br>
            - 常用于运行系统，如：<br>
            - docker run -it centos /bin/bash<br>

        - -p 指定容器端口<br>（有两种）<br>
            - （主机端口:容器端口）例如：-p 8080:8080(常用)
            - （容器端口） -p 8080

        - -P（大p） 随机指定端口
#### 2.列出所有正在运行的容器
- docker ps (当前运行的)
    - 可选参数：
        - -a 当前运行的镜像+历史运行的镜像
        - -n=**（几个）** 列出最近创建的几个容器
        - -q 只显示容器编号

#### 3.退出容器
- **exit** 退出及停止
- **Ctrl + p + q** 退出容器但不停止

#### 4.删除容器
- docker rm **容器id**

#### 5.再次启动和停止容器操作
- docker start **容器id** 
    - 启动容器
- docker stop **容器id**
    - 停止容器
- docker retart **容器id**
    - 重启容器
- docker kill **容器id**
    - 停止当前运行的容器

#### 6.进入当前正在运行的容器<br>步骤：
- 1.先查看当前正在运行的容器 **docker ps**
- 2.两种进入方法：
    - 方法一：<br>docker exec -it **容器id** /bin/bash<br>  
        - (进入容器默认开启一个新的终端)
    - 方法二：<br>
    docker attach **容器id**<br>
        - (进入正在执行的终端，不创建新终端)

#### 7.从容器复制文件到主机上<br>步骤：
- 1.进入容器内部 docker attach **容器id**
- 2.创建或查看需要复制的文件路径，退出exit
- 3.将文件拷贝到主机（容器运不运行都行）
    - 主机> cp **容器id:/home/...** /home/...(主机路径)

#### 8.打包和导入容器
- 1.打包容器
	>docker export 容器id > 文件名（自己起）.tar<br>
	>[root@XXX] # docker export s5f4dv5s6fv > ubuntu.tar   (导出到xxx目录中)

- 2.导入容器到docker中
    >cat 文件名.tar | docker import - 镜像用户(自己起)/镜像名(自己喜欢)：镜像版本号（自己设定版本）<br>
    >[root@XXX] # cat ubuntu.tar | docker import - myuser/ubuntu:v1


### 三、查看容器内的ip
- 在容器内安装 **iproute2** 这个应用，再通过 **ip addr** 命令访问
<br>

### 四、vscode 使用 docker
<br>

#### 1.安装VsCode插件<br>
搜索安装：<br>
"Docker"<br>
"Remote - Containers"<br>
"Remote - ssh"<br>

#### 2.点击VsCode左侧，"Docker"图标，发现无法连接:
- 直接使用 super用戶 打開 vscode 就可以避免這種狀況,super用戶打開vscode的命令是:</br>
    sudo code  --no-sandbox --user-data-dir