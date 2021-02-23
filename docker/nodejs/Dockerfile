FROM node:14.15.1-alpine3.10


RUN apk update
RUN apk add \
        build-base \
        libpng-dev \
        nasm \
        libtool \
        autoconf \
        automake \
        jq \
        openssh

VOLUME ["/var/www"]
WORKDIR /var/www
