ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8

RUN apt-get update  && apt-get install -y --no-install-recommends       weechat-curses       ca-certificates       jq  && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /data/weechat

COPY rootfs/ /
