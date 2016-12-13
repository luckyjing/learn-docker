FROM luckyjing/ubuntu
MAINTAINER luckyjing <luckyjing915@163.com>
ENV REFRESHED_AT 2016-12-13


# 安装Hexo
RUN cnpm install -g hexo-cli

# 编译好后的静态文件所在卷
VOLUME /usr/share/nginx/html/site

WORKDIR /usr/share/nginx/html/site

# 项目部署内容

# 安装依赖
# RUN cnpm install

# 构建
ENTRYPOINT ["hexo","generate","-w"]
