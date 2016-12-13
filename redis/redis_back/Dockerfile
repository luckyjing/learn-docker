FROM luckyjing/redis
MAINTAINER luckyjing <luckyjing915@163.com>
ENV REFRESHED_AT 2016-12-13

# redis采用主-副模式，此镜像构建的container会自动去连接 redis_primary 主服务器

ENTRYPOINT ["redis-server","--logfile /var/log/redis/redis-back.log","--slaveof redis_primary 6379"]
