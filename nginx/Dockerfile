FROM nginx:1.13.6-alpine

RUN apk update && \
    apk add certbot s6 && \
    mkdir /var/log/s6 && \
    mkdir /var/log/s6/cron && \
    mkdir /var/log/s6/nginx
