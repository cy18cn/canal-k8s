FROM java:8-alpine
MAINTAINER ryan.cao@airparking.cn

# Install base packages
RUN apk update && apk add curl bash tree tzdata \
    && cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && echo -ne "Alpine Linux 3.4 image. (`uname -rsv`)\n" >> /root/.built

RUN apk add --update coreutils && rm -rf /var/cache/apk/*

ADD canal.deployer-1.1.3.tar.gz /usr/local/canal
COPY logback.xml /usr/local/canal/conf
COPY docker-entrypoint.sh /usr/local/canal/bin
RUN chmod a+x /usr/local/canal/bin/docker-entrypoint.sh
RUN rm -rf /usr/local/canal/conf/example

WORKDIR /usr/local/canal

# 2222 sys , 8000 debug , 11111 canal , 11112 metrics
EXPOSE 2222 11111 8000 11112
ENTRYPOINT ["bin/docker-entrypoint.sh"]