FROM ubuntu:18.04

RUN apt-get update \
    && apt-get install -y nginx \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && echo "daemon off;" >> /etc/nginx/nginx.conf \
    && unlink /etc/nginx/sites-enabled/default

COPY reverse-proxy-influxdb.config /etc/nginx/sites-available/reverse-proxy.config
RUN ln -s /etc/nginx/sites-available/reverse-proxy.config /etc/nginx/sites-enabled/reverse-proxy.conf

# Certificate
COPY cert.crt  /etc/ssl/certs/localhost.crt
COPY cert.key /etc/ssl/private/localhost.key


EXPOSE 80
CMD ["nginx"]