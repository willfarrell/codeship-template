FROM willfarrell/codeship-scripts AS scripts

FROM docker:18-git

ARG workdir=/var/src
ARG bin=/usr/local/bin/codeship

ENV PATH="${PATH}:${bin}"

COPY --from=scripts /libressl/ /
COPY --from=scripts /bin/ ${bin}/
COPY bin/ ${bin}/

WORKDIR ${workdir}
