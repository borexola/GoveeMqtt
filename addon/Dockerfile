# fallback defaults for local build
ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:2025.09.0

FROM $BUILD_FROM
# copy in your binary and startup script
COPY run.sh /run.sh
RUN chmod +x /run.sh

ARG APP_IMAGE=ghcr.io/borexola/goveemqtt:latest
FROM ${APP_IMAGE} AS app

COPY --from=app /app/govee /app/
COPY --from=app /app/assets /app/assets/
COPY --from=app /app/AmazonRootCA1.pem /app/

CMD [ "/run.sh" ]
