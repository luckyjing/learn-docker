# Version 0.0.1
FROM ubuntu:14.04
MAINTAINER LuckyJing "luckyjing915@163.com"
ENV REFRESHED_AT 2016-12-12
ADD sources.list /etc/apt/sources.list
RUN apt-get clean && apt-get update && apt-get install -y nginx
RUN echo 'Hi,Docker' > /usr/share/nginx/html/index.html
ONBUILD COPY . /usr/share/nginx/html
EXPOSE 80
ENTRYPOINT ["/usr/sbin/nginx","-g","daemon off;"]
