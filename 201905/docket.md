## 前置Linux基础
* C-c中断运行中的前台程序
* \> 重定向符号
    echo "hello" 输出到终端
    echo "hello" > a.txt 输出到文件 a.txt


## 手动启动容器
### 手动启动容器
命令：
`docker run -d -t -p 8000:5000 --name demo ubuntu:18.04`

* run 表示启动一个新的 Docker 容器
* -d 让容器在后台运行
* -t 极少能用到，用于让一个空白的ubuntu镜像在后台运行
* -p 指定端口映射，表示8000端口会被自动转到容器中的5000端口，必须保证本机没有其他程序占用了8000端口，否则会失败
* -name demo指定容器的名字
* Ubuntu 18.04是启动容器的镜像名
<br>
Docker 会自动从镜像服务器下载这个镜像

### 启动容器常见问题
1. 占用3456端口，
2. 运行一个3456端口的容器，会发现因为端口被占用而失败
3. 删除 test 容器来关闭对3456端口的占用
    `docker rm -f test`
4. 再次运行容器发现依然失败，因为名字已经存在
5. 要么改名字要么删除容器重来
    * 改名字
    `docker run -t -d -p 3456 --name test2 ubuntu:18.04`
    * 删除容器
    `docker rm test1`
    `docker run -t -d -p 3456 --name test1 ubuntu:18.04`

### 在容器中安装必备软件
* ex: flask web 程序
* 用 exec 参数在运行中的Docker容器里面执行命令安装必要的依赖库

docker exec demo apt update
docker exec demo apt -y install python3 python3-pip
docker exec demo pip3 install flask



###  在容器中运行web程序
* 创建并把 a.py 拷贝到demo 容器的/code/a.py
        docker exec demo mkdir /code
        docker cp a.py "demo:/code/a.py"

* 在容器 demo 中运行 a.py <br>
`docker exec demo python3 /code/a.py`

### 脚本方式配置容器
