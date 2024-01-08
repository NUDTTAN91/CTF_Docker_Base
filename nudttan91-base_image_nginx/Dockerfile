FROM nginx:alpine

LABEL Author="tan91"
LABEL GitHub="https://github.com/NUDTTAN91"
LABEL Blog="zxw-nudt.blog.csdn.net"

COPY html /var/www/html

COPY file /tmp/

RUN mv /tmp/flag.sh /flag.sh \
    && mv /tmp/docker-entrypoint /usr/local/bin/docker-entrypoint \
    && chmod +x /usr/local/bin/docker-entrypoint \
    && mv /tmp/nginx.conf /etc/nginx/nginx.conf

WORKDIR /var/www/html

CMD ["/bin/sh", "-c", "docker-entrypoint"]

EXPOSE 80
