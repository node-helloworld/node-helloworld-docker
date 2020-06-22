FROM docker.io/bitnami/minideb:buster
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV PATH="/opt/bitnami/node/bin:/opt/bitnami/python/bin:/opt/bitnami/common/bin:/opt/bitnami/canary/bin:/opt/bitnami/nami/bin:$PATH"

COPY prebuildfs /
# Install required system packages and dependencies
RUN install_packages ca-certificates curl ghostscript gzip imagemagick libbz2-1.0 libc6 libffi6 libgcc1 liblzma5 libncursesw6 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo6 net-tools procps sudo tar zlib1g
RUN /build/bitnami-user.sh
RUN /build/install-nami.sh
RUN bitnami-pkg install node-12.18.1-0 --checksum f0ea0986d229d2b31f7f39e13955ee9a92c10ad1620dede0c1a4e55f3fa55493
RUN bitnami-pkg install tini-0.19.0-0 --checksum 9a8ae20be31a518f042fcec359f2cf35bfdb4e2a56f2fa8ff9ef2ecaf45da80c
RUN bitnami-pkg install gosu-1.12.0-0 --checksum 582d501eeb6b338a24f417fededbf14295903d6be55c52d66c52e616c81bcd8c
RUN bitnami-pkg unpack canary-1.1.3-0 --checksum a341547947975c4cf65c41dc8d0bbacfcd41f116faf3086b55044cf8d6b7751c
RUN apt-get update && apt-get upgrade -y && \
    rm -r /var/lib/apt/lists /var/cache/apt/archives

COPY rootfs /
ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.1.3-debian-10-r24" \
    CANARY_HELLONAME="world" \
    OS_ARCH="amd64" \
    OS_FLAVOUR="debian-10" \
    OS_NAME="linux"

EXPOSE 3000 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary" ]
