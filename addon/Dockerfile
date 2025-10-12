# fallback defaults so local builds work
ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:2025.09.0
ARG APP_IMAGE=ghcr.io/borexola/goveemqtt:latest

# stage: copy from your compiled app image
FROM ${APP_IMAGE} AS app

# this is the runtime base image that the HA builder will override
FROM ${BUILD_FROM}

# copy everything you need from the app stage
COPY --from=app /app/govee /app/
COPY --from=app /app/assets /app/assets/
COPY --from=app /app/AmazonRootCA1.pem /app/

# include your startup script
COPY run.sh /run.sh
RUN chmod +x /run.sh

CMD ["/run.sh"]
