FROM bitnami/minideb-extras:stretch-r205
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.14.4-2 --checksum ad88cd21120c64e122feac5c0f5c33d7ceb85ecd78c5263baaaa95554a9b1d3d
RUN bitnami-pkg unpack canary-1.0.15-1 --checksum 7b9b74ddd08936dd17d400c348c983880490508ba2b3db143c4fe98528809c32

COPY rootfs /
ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.15-debian-9-r31" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary" ]
