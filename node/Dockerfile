FROM willfarrell/codeship-base AS base

FROM node:12-alpine

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

ENV PATH=${PATH}:${bin}:${workdir}/node_modules/.bin

# rsync faster than cp, when running locally
RUN apk update && \
    apk add --no-cache bash openssl git openssh-client \
    rsync

COPY --from=base ${bin}/ ${bin}/

WORKDIR ${workdir}
