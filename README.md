# docker

run: `docker-compose up`

stop: `docker-compose down`

### 构建前端镜像

首先按照Docker文档在根目录下新建并编写Dockerfile，其中规定使用环境为Node:10，这样就不会自动拉取最新版本的node导致错误；并且规定启动docker运行时执行npm install安装依赖，这里要注意不能在构建镜像的文件夹下包含node_modules，这样会让镜像变得很大，只需要在构建时下载即可；最后构建完毕后运行时执行npm run serve，规定把前端部分运行在8081端口。

在目录下执行命令`sudo docker build -t goswapifront .`构建镜像，指定镜像名称为goswapifront，构建成功后可以在docker的镜像列表中看到该镜像，最后用`docker run -d -p 8081:8081 goswapifront`在后台运行镜像，其中指定主机的8081端口映射到容器的8081端口，这样就成功启动了镜像。

在整个项目中为了运行docker-compose，需要编写compose的约束文件，指定前端镜像的文件夹，只要改文件夹下包含dockerfile，这一部分就可以正确运行了。
