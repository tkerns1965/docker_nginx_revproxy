ARG NGINX_VERSION
FROM nginx:${NGINX_VERSION}

RUN apk update && \
    apk add certbot s6 && \
    mkdir -p /var/log/s6/cron && \
    mkdir -p /var/log/s6/nginx

COPY s6 /etc/s6
COPY *.conf /etc/nginx/conf.d/
# COPY *.html /usr/share/nginx/html/
COPY crontab_certbot /root/

RUN (crontab -l ; cat /root/crontab_certbot) | crontab - && \
    rm /root/crontab_certbot

CMD ["s6-svscan", "/etc/s6"]
