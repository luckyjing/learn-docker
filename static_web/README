`Dockerfile`由一系列指令和参数组成，指令必须大写。

## 执行流程

- 从基础镜像运行一个容器
- 执行一条指令，对容器作出修改
- 执行一次`docker commit`，提交一个新的镜像层
- 接着刚才提交的镜像层继续做下一个操作
- 直到命令执行完毕

## 小技巧提高构建速度

我们使用的`ubuntu`镜像默认`apt-get`方式是从其官网镜像构建的，国内往往访问速度过慢，所以我们需要在执行`apt-get`之前换源，这里我们用的是`阿里云镜像`

```bash
ADD sources.list /etc/apt/sources.list
```

## 执行方式

在当前目录下执行`docker build -t [NAME] .`

## 命名规范

采用`[镜像名：标签]`的方式为其命名，也就是说，我们可以命名为以下形式

```bash
docker build -t luckyjing/static_web:v1
docker build -t luckyjing/static_web   # 不携带 :xx 时默认用 latest标签
```

## 查看产出

现在通过执行`docker images`来看到我们新产出的镜像

```bash
docker run -t -i --name static luckyjing/static_web /bin/bash
```

## 感受构建缓存

我们再一次执行构建命令，发现会非常快，因为`Docker`将没有更改的每一次提交直接就快速略过了，这类似于`Git`里面合并的`Fast Forward`模式。

有时候我们会有这种需求，对于某些步骤，我希望其能够在构建时重新执行，比如获取资源包`apt-get`，实现的方法也很简单，也是利用`Docker`是将每一次命令执行后的版本缓存的特性，我们在`A-B-C-D`这个命令串中，加入`A-B-B1-C-D`,那么在执行完`B1`之后，将会得到一个全新的`commit`信息，随后`C-D`将会全新执行，而不会被缓存。

这个`B1`任务可以是一个与业务无关的任务，例如`The Docker Book`推荐的方法，仅仅是设置一个对开发者友好的时间记录。

```bash
ENV REFRESHED_AT 2016-12-12
```

## 删除全部container

```bash
docker rm `docker ps -s -a` # ``包裹的命令返回全部的容器ID，这样便可以巧妙地一次性删除完毕
```
