FROM alpine:3.11
EXPOSE 3000
RUN apk update
RUN apk add wget libc6-compat
RUN wget https://dl.grafana.com/oss/release/grafana-6.5.0.linux-amd64.tar.gz
RUN tar -zxvf grafana-6.5.0.linux-amd64.tar.gz
RUN rm -rf grafana-6.5.0.linux-amd64.tar.gz
RUN mv grafana-6.5.0 grafana
COPY ./grafana.db /grafana/data/grafana.db

RUN apk add telegraf --no-cache --repository http://dl-2.alpinelinux.org/alpine/edge/community
RUN mkdir -p /etc/telegraf/
COPY ./telegraf.conf /etc/telegraf/telegraf.conf
COPY ./healthy.sh /
COPY start.sh /
CMD ["sh", "start.sh"]