FROM php:7.3-fpm-alpine

LABEL Author="tan91"
LABEL GitHub="https://github.com/NUDTTAN91"
LABEL Blog="zxw-nudt.blog.csdn.net"

COPY files /tmp/
COPY html /var/www/html

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
    && apk add --update --no-cache nginx \
    && mkdir -p /run/nginx \
    # configure file
    && mv /tmp/flag.sh /flag.sh \
    && mv /tmp/docker-php-entrypoint /usr/local/bin/docker-php-entrypoint \
    && chmod +x /usr/local/bin/docker-php-entrypoint \
    && mv /tmp/nginx.conf /etc/nginx/nginx.conf \
    && chown -R www-data:www-data /var/www/html \
    # clear
    && rm -rf /tmp/*

WORKDIR /var/www/html

EXPOSE 80

VOLUME ["/var/log/nginx"]

CMD ["/bin/bash", "-c", "docker-php-entrypoint"]