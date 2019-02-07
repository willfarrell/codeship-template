FROM willfarrell/libressl:latest AS libressl
FROM scratch
COPY --from=libressl /libressl/ /libressl/
COPY bin/ /bin
