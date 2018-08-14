FROM bitnami/minideb-extras:stretch-r106
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.14.3-0 --checksum 2759392d63fcf4a6c9322b79546a4655a2a2e8fa267bb169c2c64edb12ed6875
RUN bitnami-pkg unpack canary-1.0.14-0 --checksum 2c7ce21f99fee069fb543c3fbdf381b838fcdc83b96d73fa4aedde0ad8aa63ad

COPY rootfs /
ENV BITNAMI_APP_NAME="canary" \
    BITNAMI_IMAGE_VERSION="1.0.14-debian-9-r5" \
    CANARY_HELLONAME="world" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","canary"]