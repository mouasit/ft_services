FROM alpine:3.11
EXPOSE 3306
RUN apk update
RUN apk add openrc mariadb mariadb-client
COPY mariadb-server.cnf /etc/my.cnf.d/
COPY ./phpmyadmin.sql /
COPY ./wordpress.sql /
RUN apk add telegraf --no-cache --repository http://dl-2.alpinelinux.org/alpine/edge/community
RUN mkdir -p /etc/telegraf/
COPY ./telegraf.conf /etc/telegraf/telegraf.conf
COPY ./healthy.sh /
COPY start.sh /
CMD ["sh","start.sh"]