# Dockerfile
Dockerfile 是一个用来构建镜像的文本文件，文本内容包含了一条条构建镜像所需的指令和说明。

## 构建第一个镜像

### 创建一个Dockerfile
``` Dockerfile
FROM nginx:latest
RUN echo '这是一个本地构建的nginx镜像' > /usr/share/nginx/html/index.html
```

### 构建镜像
```
docker build -t nginx-local:latest .
```
通过目录下的 Dockerfile 构建一个 nginx-local:latest（镜像名称:镜像标签）。

**注意**最后的的```.```是代表本次执行的上下文路径。

上下文路径，是指 docker 在构建镜像，有时候想要使用到本机的文件（比如复制），docker build 命令得知这个路径后，会将路径下的所有内容打包。

## 添加文件到镜像

### 修改Dockerfile
``` Dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/
```
这里我们使用```COPY```指令，从上下文目录中复制文件或者目录到容器里指定路径。

### ```COPY``` 指令 
```
COPY [--chown=<user>:<group>] <源路径1>...  <目标路径>
COPY [--chown=<user>:<group>] ["<源路径1>",...  "<目标路径>"]
```

> <源路径>：源文件或者源目录，这里可以是通配符表达式，其通配符规则要满足 Go 的 filepath.Match 规则。例如：
``` Dockerfile
COPY hom* /mydir/
COPY hom?.txt /mydir/
```

## 添加文件夹到镜像

### 修改Dockerfile
``` Dockerfile
FROM nginx:latest
Add ./html /usr/share/nginx/html/
```

```ADD``` 指令和 COPY 的使用格类似（同样需求下，官方推荐使用 COPY）。功能也类似，不同之处如下：
```ADD``` 的优点：在执行 <源文件> 为 tar 压缩文件的话，压缩格式为 gzip, bzip2 以及 xz 的情况下，会自动复制并解压到 <目标路径>。
```ADD``` 的缺点：在不解压的前提下，无法复制 tar 压缩文件。会令镜像构建缓存失效，从而可能会令镜像构建变得比较缓慢。具体是否使用，可以根据是否需要自动解压来决定。
