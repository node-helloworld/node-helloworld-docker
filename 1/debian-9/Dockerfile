FROM bitnami/minideb-extras:stretch-r218
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.15.1-0 --checksum 34fa4d22ac666cb638b0f7dd07d61b72e284735454d17aff9102541b7c6d6ae1
RUN bitnami-pkg unpack canary-1.0.15-20 --checksum ac410d24d20de02b3f0b8961faffbb268a062451a111bad761fa50a8fe3cc4ec

COPY rootfs /
ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.15-debian-9-r49" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary" ]
