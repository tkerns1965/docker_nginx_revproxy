ARG APACHE_VERSION
FROM httpd:${APACHE_VERSION}

COPY *.html /usr/local/apache2/htdocs/

RUN sed -i 's/index.html/web2.html/' /usr/local/apache2/conf/httpd.conf
