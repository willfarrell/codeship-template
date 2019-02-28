FROM willfarrell/codeship-base AS base

FROM node:8-alpine

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

ENV PATH=${PATH}:${bin}:${workdir}/node_modules/.bin

# rsync faster than cp, when running locally
RUN apk add --no-cache openssl git openssh-client

# `aws`
# https://pypi.org/project/awscli/
ARG awscli=1.16.109

RUN apk add --no-cache --virtual .deps python groff && \
    apk add --no-cache --virtual .build-deps py-pip && \
    pip install --upgrade awscli==${awscli} && \
    apk -v --purge del .build-deps

RUN npm i -g serverless

COPY --from=base ${bin}/ ${bin}/

WORKDIR ${workdir}