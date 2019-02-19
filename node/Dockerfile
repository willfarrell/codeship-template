FROM willfarrell/codeship-base AS base

FROM node:8-alpine

ARG workdir=/data
ARG bin=/usr/local/bin/codeship

ENV PATH=${PATH}:${bin}:${workdir}/node_modules/.bin

# rsync faster than cp, when running locally
RUN apk add --no-cache openssl git openssh-client \
    rsync

# Prevent `EMFILE: too many open files, scandir`
# https://stackoverflow.com/questions/8965606/node-and-error-emfile-too-many-open-files
#RUN ulimit -Sn 65536
#RUN echo "session required pam_limits.so" >> /etc/pam.d/common-session
#RUN echo "root soft  nofile 40000" >> /etc/security/limits.conf
#RUN echo "root hard  nofile 100000" >> /etc/security/limits.conf

COPY --from=base ${bin}/ ${bin}/

WORKDIR ${workdir}
