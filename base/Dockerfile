FROM alpine:3.9

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

ENV PATH="${PATH}:${bin}"

RUN apk add --no-cache bash openssl git openssh-client

COPY bin/ ${bin}/

WORKDIR ${workdir}
