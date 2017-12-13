ARG NGINX_VERSION
FROM nginx:${NGINX_VERSION}

RUN apk update && \
    apk add certbot s6 && \
    mkdir /var/log/s6 && \
    mkdir /var/log/s6/cron && \
    mkdir /var/log/s6/nginx

COPY s6 /etc/s6
COPY crontab_certbot /root/
COPY *.conf /etc/nginx/conf.d/

RUN (crontab -l ; cat /root/crontab_certbot) | crontab -

CMD ["s6-svscan", "/etc/s6"]
