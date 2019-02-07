FROM willfarrell/codeship-scripts AS scripts

FROM node:8
COPY --from=scripts /libressl/ /
COPY --from=scripts /bin/ /usr/local/bin/

ARG workdir=/var/src

RUN export PATH=$PATH:${workdir}/node_modules/.bin

WORKDIR ${workdir}
