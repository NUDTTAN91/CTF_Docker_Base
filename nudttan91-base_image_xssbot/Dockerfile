FROM node:alpine

LABEL Author="tan91"
LABEL GitHub="https://github.com/NUDTTAN91"
LABEL Blog="zxw-nudt.blog.csdn.net"

ENV LANG="C.UTF-8" PUPPETEER_SKIP_CHROMIUM_DOWNLOA=true

# sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/' /etc/apk/repositories && \

RUN apk update
RUN apk add --no-cache zlib-dev udev nss ca-certificates chromium
RUN yarn add puppeteer-core
RUN adduser -h /home/bot -D -u 10086 bot
RUN yarn cache clean
RUN rm -rf /tmp/* /etc/apk/* /var/cache/apk/* /usr/share/man

COPY --chown=bot:bot ./app.js /home/bot/app.js

USER bot
WORKDIR /home/bot

CMD ["node", "/home/bot/app.js"]