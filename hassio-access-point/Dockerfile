ARG BUILD_FROM=ghcr.io/home-assistant/base:latest
ARG BUILD_VERSION=0.5.4

FROM ${BUILD_FROM}

# Labels (ersetzen MAINTAINER)
LABEL \
    io.hass.name="Hassio Access Point" \
    io.hass.description="Create a WiFi access point using hostapd" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="ex_ml@sent.com"

RUN apk update && \
apk add --no-cache bash iw hostapd networkmanager networkmanager-cli net-tools sudo dnsmasq iptables && \
rm -rf /var/cache/apk/*

COPY hostapd.conf /
COPY dnsmasq.conf /

COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
