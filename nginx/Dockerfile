FROM nginx:stable-alpine

LABEL org.opencontainers.image.source https://github.com/silvenga-docker/matomo-host

COPY rootfs/ /

EXPOSE 80
STOPSIGNAL SIGTERM
