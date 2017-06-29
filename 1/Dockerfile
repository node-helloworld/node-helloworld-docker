FROM bitnami/minideb-extras:jessie-r19
LABEL maintainer "Bitnami <containers@bitnami.com>"



# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libmysqlclient18 libncurses5 libreadline6 libsqlite3-0 libssl1.0.0 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.11.0-0 --checksum 203d22e3357eb5e8573c8d95691f01e1a2a3badcfc2baee0bf83b3ad91dfeb86
RUN bitnami-pkg unpack canary-1.0.12-0 --checksum f71c760592d6ede64a033e61af78f226cb5ea2a49f26fc5b9c61af5aa664d0f4

COPY rootfs /

ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.12-r0" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"



VOLUME ["/bitnami/canary"]

EXPOSE 8080

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","canary"]
