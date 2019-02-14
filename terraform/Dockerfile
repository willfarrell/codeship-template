FROM willfarrell/codeship-scripts AS scripts

FROM hashicorp/terraform:0.11.11

ARG workdir=/var/src
ARG bin=/usr/local/bin/codeship

ENV PATH="${PATH}:${bin}"

COPY --from=scripts /libressl/ /
COPY --from=scripts /bin/ ${bin}/
COPY bin/ ${bin}/

WORKDIR ${workdir}
