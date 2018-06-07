FROM bitnami/minideb-extras:jessie-r69
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libmysqlclient18 libncurses5 libreadline6 libsqlite3-0 libssl1.0.0 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.14.2-0 --checksum 090668f178d5ea72e2892ee6a1451175f3ad9692132651c33c06c839d7b74170
RUN bitnami-pkg unpack canary-1.0.13-1 --checksum 4c8cf5596698d49fd79e7174f5a1b1aa427c829e11ac7798431519a4d2de0783

COPY rootfs /
ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.13-r45" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","canary"]
