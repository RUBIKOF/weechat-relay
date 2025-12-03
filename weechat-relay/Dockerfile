ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8
ENV TERM=xterm

RUN apk add --no-cache \
      weechat \
      ca-certificates \
      jq

COPY rootfs/ /

RUN chmod +x /etc/services.d/weechat/run
