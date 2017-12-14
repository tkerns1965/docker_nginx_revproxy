ARG NGINX_VERSION
FROM nginx:${NGINX_VERSION}

RUN apk update && \
    apk add certbot s6 && \
    mkdir -p /var/log/s6/cron && \
    mkdir -p /var/log/s6/nginx

COPY s6 /etc/s6
COPY *.conf /etc/nginx/conf.d/
COPY revproxy.html /usr/share/nginx/html/

COPY crontab_certbot /root/
RUN (crontab -l ; cat /root/crontab_certbot) | crontab - && \
    rm /root/crontab_certbot && \
    sed -i 's/index.html index.htm/revproxy.html/' /etc/nginx/conf.d/default.conf && \
    sed -i 's/%_WEB1_%/web1.$NGINX_DOMAIN/' /etc/nginx/conf.d/web1.conf && \
    sed -i 's/%_WEB2_%/web2.$NGINX_DOMAIN/' /etc/nginx/conf.d/web2.conf

CMD ["s6-svscan", "/etc/s6"]
