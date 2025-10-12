ARG BUILD_FROM
FROM ghcr.io/borexola/goveemqtt:latest AS goveemqtt
FROM $BUILD_FROM
COPY run.sh /run.sh
COPY --from=goveemqtt /app/govee /app/
COPY --from=goveemqtt /app/assets /app/assets/
COPY --from=goveemqtt /app/AmazonRootCA1.pem /app/
CMD [ "/run.sh" ]
