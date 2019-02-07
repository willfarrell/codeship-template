FROM willfarrell/libressl AS libressl
FROM buildpack-deps:stretch
COPY --from=libressl /libressl/ /
COPY bin/ /bin/
