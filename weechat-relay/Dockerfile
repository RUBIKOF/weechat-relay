ARG BUILD_FROM
FROM ${BUILD_FROM}

# Configuración de entorno
ENV LANG=C.UTF-8
ENV TERM=xterm

# Instalación de WeeChat + plugin relay + jq
RUN apt-get update && apt-get install -y --no-install-recommends \
      weechat-curses \
      weechat-plugins \
      ca-certificates \
      jq \
 && rm -rf /var/lib/apt/lists/*

# Crear directorio de configuración interno
RUN mkdir -p /data/weechat

# Copiar rootfs del add-on
COPY rootfs/ /

# Dar permisos al script de inicio
RUN chmod +x /etc/services.d/weechat/run
