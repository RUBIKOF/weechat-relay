ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8
ENV TERM=xterm-256color

# Instalar WeeChat en Alpine
RUN apk add --no-cache \
      weechat \
      ncurses-terminfo-base \
      ca-certificates \
      jq

# Copiamos rootfs (scripts de s6)
COPY rootfs/ /

# Aseguramos permisos de ejecución del servicio
RUN chmod +x /etc/services.d/weechat/run
