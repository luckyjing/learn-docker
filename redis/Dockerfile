# Version 0.0.1

FROM ubuntu:14.04
MAINTAINER LuckyJing "luckyjing915@163.com"
ENV REFRESHED_AT 2016-12-12
ADD sources.list /etc/apt/sources.list

# base dependencies

RUN apt-get clean && apt-get update
RUN apt-get install -yqq software-properties-common python-software-properties
RUN add-apt-repository ppa:chris-lea/redis-server
RUN apt-get -yqq update
RUN apt-get -yqq install redis-server redis-tools

VOLUME ["/var/lib/redis","/var/log/redis/"]

EXPOSE 6379

CMD []
