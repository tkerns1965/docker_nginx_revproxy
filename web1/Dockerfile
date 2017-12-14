ARG NGINX_VERSION
FROM nginx:${NGINX_VERSION}

COPY web1.html /usr/share/nginx/html/

RUN sed -i 's/index.html index.htm/web1.html/' /etc/nginx/conf.d/default.conf
