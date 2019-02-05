FROM node:8

COPY docker-entrypoint /
ENTRYPOINT ["/docker-entrypoint"]

WORKDIR /var/src

RUN export PATH=$PATH:/var/src/node_modules/.bin

# TODO RUN npm i {scans}
