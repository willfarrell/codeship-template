FROM willfarrell/codeship-scripts AS scripts

FROM docker:18-git
COPY --from=scripts /libressl/ /

ARG workdir=/var/src
ARG bin=/usr/local/bin/codeship

ENV PATH="${PATH}:${bin}"

COPY bin/ ${bin}/
#COPY --from=scripts /bin/ ${bin}/

WORKDIR ${workdir}
