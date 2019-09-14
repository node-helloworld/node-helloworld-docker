FROM bitnami/minideb-extras:stretch-r479
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.17.1-1 --checksum 9fa6fe4549acf64f94e22154de7bf8e0bc93b95961fa8294f906b5d3677b625b
RUN bitnami-pkg unpack canary-1.0.15-21 --checksum d2a78ab0fbca5a3f7661afdb0d4684449acec3f1d992b675cc38fcfe8cac4688

COPY rootfs /
ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.15-debian-9-r307" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary" ]
