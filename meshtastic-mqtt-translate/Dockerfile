ARG BUILD_FROM
FROM ${BUILD_FROM}

ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION
ARG TEMPIO_VERSION
ARG MQTT_RELAY_VERSION

RUN \
   curl -sSLf -o /meshtastic-mqtt-relay.tar.gz \
	 "https://github.com/na4ma4/meshtastic-mqtt-translate/releases/download/v${MQTT_RELAY_VERSION}/meshtastic-mqtt-translate_${MQTT_RELAY_VERSION}_linux_${BUILD_ARCH}.tar.gz" \
	 && mkdir -p /opt/mqtt-relay \
	 && tar -xzf /meshtastic-mqtt-relay.tar.gz -C /opt/mqtt-relay

# Execute during the build of the image
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}" \
    && chmod a+x /usr/bin/tempio

# Copy root filesystem
COPY rootfs /

LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Na4Ma4 <na4ma4@noreply.users.github.com>"