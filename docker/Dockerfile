FROM willfarrell/codeship-base AS base

FROM docker:18-dind

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

ENV PATH="${bin}:${PATH}:${bin}"

RUN apk update && \
    apk add --no-cache openssl bash git openssh-client

WORKDIR ${workdir}

# ARG pass=1.7.3

# https://github.com/docker/docker-credential-helpers
# https://github.com/gopasspw/gopass
# Install pass - https://www.passwordstore.org/
#RUN apk -v --update add curl tar alpine-sdk build-base make && \
#    curl -sL https://github.com/zx2c4/password-store/archive/${pass}.tar.gz | tar xz && \
#    cd password-store-${pass} && make install && cd .. && \
#    rm -rf password-store-${pass} && \
#    apk -v --purge del curl tar alpine-sdk buiold-base make && \
#    rm /var/cache/apk/*

COPY --from=base ${bin}/ ${bin}/
