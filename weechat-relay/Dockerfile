ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8
ENV TERM=xterm-256color

# Instalar WeeChat y herramientas necesarias en Alpine
RUN apk add --no-cache \
      weechat \
      ncurses-terminfo-base \
      ca-certificates \
      jq

# Copiamos los servicios s6 (nuestro script de arranque)
COPY rootfs/ /
