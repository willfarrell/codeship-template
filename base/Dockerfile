FROM alpine:3.10

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

ENV PATH="${PATH}:${bin}"

#  gzip and brotli for pre-compressing static assets (aws-s3-deploy)
RUN apk update && \
    apk add --no-cache bash jq openssl git openssh-client && \
    apk add --no-cache gzip brotli

COPY bin/ ${bin}/

WORKDIR ${workdir}
