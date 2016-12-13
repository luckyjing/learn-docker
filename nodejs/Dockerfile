# Version 0.0.1

FROM ubuntu:14.04
MAINTAINER LuckyJing "luckyjing915@163.com"
ENV REFRESHED_AT 2016-12-12
ADD sources.list /etc/apt/sources.list

# base dependencies

RUN apt-get clean && apt-get update && apt-get install -y nginx
RUN apt-get install -yqq curl python gcc make g++ wget

# install Node.js

RUN wget https://npm.taobao.org/mirrors/node/v4.6.0/node-v4.6.0-linux-x64.tar.gz
RUN tar -xzvf node-v4.6.0-linux-x64.tar.gz
RUN rm -rf node-v4.6.0-linux-x64.tar.gz
RUN mv node-v4.6.0-linux-x64 /opt/
RUN ln -s /opt/node-v4.6.0-linux-x64/bin/node /usr/local/bin/node
RUN ln -s /opt/node-v4.6.0-linux-x64/bin/npm /usr/local/bin/npm
RUN npm install -g cnpm --registry=https://registry.npm.taobao.org
RUN mkdir -p /var/log/nodeapp

# ENV

ENV PATH $PATH:/opt/node-v4.6.0-linux-x64/bin

# Project Settings
ADD app /opt/nodeapp

WORKDIR /opt/nodeapp
RUN cnpm install

VOLUME ["/var/log/nodeapp"]

EXPOSE 3000

ENTRYPOINT ["node","server.js"]
