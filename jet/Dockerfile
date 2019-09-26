FROM docker:18-dind

ARG ARCH=amd64
ARG JET_VERSION=2.10.0
ARG workdir=/data

WORKDIR ${workdir}

RUN apk update && \
    apk add --no-cache --virtual .build-dep curl tar && \
    curl -SLO "https://s3.amazonaws.com/codeship-jet-releases/2.10.0/jet-linux_${ARCH}_${JET_VERSION}.tar.gz" && \
    tar -xaC /usr/local/bin -f jet-linux_${ARCH}_${JET_VERSION}.tar.gz && \
    rm jet-linux_${ARCH}_${JET_VERSION}.tar.gz && \
    chmod +x /usr/local/bin/jet
# TODO add back in
# WARNING: Ignoring APKINDEX.b89edf6e.tar.gz: No such file or directory
# WARNING: Ignoring APKINDEX.737f7e01.tar.gz: No such file or directory
# The command '/bin/sh -c apk del .build-deps' returned a non-zero code: 1
#    apk del .build-deps

ENTRYPOINT [ "jet" ]

CMD [ "--help" ]
