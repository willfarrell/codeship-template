#FROM willfarrell/codeship-scripts AS scripts

FROM docker:18-git
#COPY --from=scripts /libressl/ /
#COPY --from=scripts /bin/ /usr/local/bin/

ARG workdir=/var/src

COPY bin/ /usr/local/bin/

WORKDIR ${workdir}
