ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8
ENV TERM=xterm-256color

# Instalar WeeChat y terminfo para que ncurses no llore
RUN apk add --no-cache \
      weechat \
      ncurses-terminfo-base \
      ca-certificates \
      jq

# Script de arranque simple:
#  - crea /config/weechat
#  - lee options.json para puerto/contraseña
#  - configura relay si hace falta
#  - lanza weechat como daemon
#  - mantiene contenedor vivo con tail -f
CMD ["/bin/sh", "-c", "\
  mkdir -p /config/weechat && \
  echo '[INFO] WeeChat config dir: /config/weechat' && \
  if [ -f /data/options.json ]; then \
    RELAY_PORT=$(jq -r '.relay_port // 9001' /data/options.json); \
    RELAY_PASSWORD=$(jq -r '.relay_password // \"cambia-esta-contraseña\"' /data/options.json); \
  else \
    RELAY_PORT=9001; \
    RELAY_PASSWORD='cambia-esta-contraseña'; \
  fi; \
  echo \"[INFO] Relay port: ${RELAY_PORT}\"; \
  if [ ! -f /config/weechat/weechat.conf ]; then \
    echo '[INFO] First start: generating config and enabling relay...'; \
    weechat -d /config/weechat --no-color --no-connect -r \"\
/set relay.network.password ${RELAY_PASSWORD}\
/set relay.network.bind_address 0.0.0.0\
/set relay.network.port ${RELAY_PORT}\
/relay add weechat 0.0.0.0/${RELAY_PORT}\
/save\
/quit\"; \
  fi; \
  echo '[INFO] Starting WeeChat daemon...'; \
  TERM=xterm-256color weechat --daemon -d /config/weechat && \
  echo '[INFO] WeeChat started, keeping container alive...' && \
  tail -f /dev/null \
"]
