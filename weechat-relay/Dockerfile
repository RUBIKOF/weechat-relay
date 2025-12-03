ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8
ENV TERM=xterm

# Instalar WeeChat en Alpine
RUN apk add --no-cache \
      weechat \
      ca-certificates \
      jq

# Arranque simple: crea config, lanza weechat como daemon y mantiene el contenedor vivo
CMD ["/bin/sh", "-c", "\
  mkdir -p /config/weechat && \
  chmod -R 777 /config/weechat && \
  echo '[INFO] Starting WeeChat daemon...' && \
  TERM=xterm weechat --daemon -d /config/weechat && \
  echo '[INFO] WeeChat started, keeping container alive...' && \
  tail -f /dev/null \
"]
