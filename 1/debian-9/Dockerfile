FROM bitnami/minideb-extras:stretch-r257
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.16.0-0 --checksum f56d388b8f711954c3516f197df46f8d7fb7791050cb3fe6650c6579dfadb894
RUN bitnami-pkg unpack canary-1.0.15-20 --checksum ac410d24d20de02b3f0b8961faffbb268a062451a111bad761fa50a8fe3cc4ec

COPY rootfs /
ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.15-debian-9-r94" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary" ]
