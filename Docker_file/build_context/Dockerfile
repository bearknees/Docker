# Stage 1: Build Stage
FROM ubuntu:latest AS builder
MAINTAINER bernicepena <qbmpena@tip.edu.ph>

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y \
        apache2 \
        php \
        libapache2-mod-php \
        mariadb-server \
        mariadb-client \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN /etc/init.d/apache2 start

# Stage 2: Final Stage
FROM ubuntu:latest
MAINTAINER bernicepena <qbmpena@tip.edu.ph>

COPY --from=builder / /

ENTRYPOINT apache2ctl -D FOREGROUND
