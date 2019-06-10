FROM alpine:3.9

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

ENV PATH="${PATH}:${bin}"

RUN apk update && \
    apk add --no-cache bash jq openssl git openssh-client

COPY bin/ ${bin}/

WORKDIR ${workdir}
