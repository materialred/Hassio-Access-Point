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

# Install required packages
RUN apk add --no-cache \
    hostapd \
    dnsmasq \
    iptables \
    iw \
    bash

# Copy root filesystem
COPY rootfs/ /

# Ensure scripts are executable
RUN chmod a+x /etc/services.d/*/run

# Default command handled by s6 (Home Assistant base image)
