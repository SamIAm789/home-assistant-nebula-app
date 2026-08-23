ARG BUILD_FROM=ghcr.io/home-assistant/amd64-addon-base:14.3.2
FROM ${BUILD_FROM}

ARG NEBULA_VERSION=1.11.1
ARG NEBULA_ARCH=linux-amd64

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apk add --no-cache ca-certificates bash curl tar

WORKDIR /tmp
RUN curl -sSL \
    -o nebula.tar.gz \
    https://github.com/slackhq/nebula/releases/download/v\( {NEBULA_VERSION}/nebula- \){NEBULA_ARCH}.tar.gz && \
    tar xzf nebula.tar.gz && \
    mv nebula nebula-cert /usr/local/bin/ && \
    chmod +x /usr/local/bin/nebula /usr/local/bin/nebula-cert && \
    rm -rf /tmp/*

# remove any docker-init shim from the image so it cannot be used as PID 1
RUN rm -f /sbin/docker-init || true

# This is all you need for s6 + services
WORKDIR /config
COPY rootfs/ /
ENTRYPOINT ["/init"]
CMD []
