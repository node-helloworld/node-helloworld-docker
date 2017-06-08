FROM bitnami/minideb-extras:jessie-r17
LABEL maintainer "Bitnami <containers@bitnami.com>"



# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libmysqlclient18 libncurses5 libreadline6 libsqlite3-0 libssl1.0.0 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.10.3-0 --checksum 07bb05274dd2cf71ebdd92ff00925bf1ff16588664e24f59a3b5ecfce7dce238
RUN bitnami-pkg unpack canary-1.0.8-0 --checksum d92fef066a3e3e663e96cc70caa45032785b87e5414634bf81c69108b8953f3f

COPY rootfs /

ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.8-r0" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"



VOLUME ["/bitnami/canary"]

EXPOSE 8080

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","canary"]
