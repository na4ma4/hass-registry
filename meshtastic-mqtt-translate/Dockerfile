ARG BUILD_FROM
FROM ${BUILD_FROM}
ARG TEMPIO_VERSION BUILD_ARCH
ARG MQTT_RELAY_VERSION=0.2.2

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
