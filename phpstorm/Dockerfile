FROM registry.access.redhat.com/ubi8/ubi-minimal:8.7

ARG JETBRAINS_VERSION

LABEL org.opencontainers.image.source=https://github.com/ThunderAl197/jetbrains-docker \
      org.opencontainers.image.version=phpstorm-$JETBRAINS_VERSION

RUN set -xe; \
    mkdir -p /opt/phpstorm; \
    cd /opt/phpstorm; \
    microdnf install -y gzip tar curl git; \
    microdnf clean all; \
    curl -s "https://download-cdn.jetbrains.com/webide/PhpStorm-$JETBRAINS_VERSION.tar.gz" -o jetbrains.tar.gz; \
    tar -xvzf jetbrains.tar.gz; \
    rm -f jetbrains.tar.gz; \
    mv */* .; \
    echo -e '#!/usr/bin/env sh\n/opt/phpstorm/bin/phpstorm.sh $@' > /usr/bin/phpstorm; \
    chmod +x /usr/bin/phpstorm; \
    echo -e '#!/usr/bin/env sh\n/opt/phpstorm/bin/remote-dev-server.sh $@' > /usr/bin/phpstorm-remote-dev-server; \
    chmod +x /usr/bin/phpstorm-remote-dev-server; \
    echo -e '#!/usr/bin/env sh\n/opt/phpstorm/bin/inspect.sh $@' > /usr/bin/phpstorm-inspect; \
    chmod +x /usr/bin/phpstorm-inspect; \
    echo -e '#!/usr/bin/env sh\n/opt/phpstorm/bin/format.sh $@' > /usr/bin/phpstorm-format; \
    chmod +x /usr/bin/phpstorm-format;

