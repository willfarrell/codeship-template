FROM willfarrell/codeship-scripts AS scripts

FROM node:8

ARG workdir=/var/src
ARG bin=/usr/local/bin/codeship

ENV PATH="${PATH}:${bin}:${workdir}/node_modules/.bin"

COPY --from=scripts /libressl/ /
COPY --from=scripts /bin/ ${bin}/
COPY bin/ ${bin}/

WORKDIR ${workdir}
