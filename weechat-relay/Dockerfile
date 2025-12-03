ARG BUILD_FROM
FROM ${BUILD_FROM}

# Entorno básico
ENV LANG=C.UTF-8
ENV TERM=xterm

# Instalamos WeeChat (headless) + plugins + utilidades
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      weechat-headless \
      weechat-plugins \
      ca-certificates \
      jq \
 && rm -rf /var/lib/apt/lists/*

# Copiamos rootfs del add-on dentro del contenedor
COPY rootfs/ /

# Nos aseguramos de que el script de servicio sea ejecutable
RUN chmod +x /etc/services.d/weechat/run
