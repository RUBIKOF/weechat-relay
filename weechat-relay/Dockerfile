ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8
ENV TERM=xterm

# Instalar WeeChat HEADLESS en Alpine (sin ncurses/TUI)
RUN apk add --no-cache \
      weechat-headless \
      ca-certificates \
      jq

# Script de arranque simple
CMD ["/bin/sh", "-c", "\
  mkdir -p /config/weechat && \
  chmod -R 777 /config/weechat && \
  echo \"[INFO] Starting WeeChat headless daemon...\" && \
  TERM=xterm weechat-headless --daemon -d /config/weechat && \
  echo \"[INFO] WeeChat started, keeping container alive...\" && \
  tail -f /dev/null \
"]
