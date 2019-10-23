ARG NODEVERSION
FROM node:${NODEVERSION}-alpine

ARG SERVERNAME

RUN apk update \
  && apk add python \
             pkgconf \
             pixman


RUN mkdir -p /srv/app/${SERVERNAME}
WORKDIR /srv/app/${SERVERNAME}

ARG APPPATH=/srv/app/${SERVERNAME}
WORKDIR ${APPPATH}
RUN mkdir -p ./src/component \
    && mkdir -p ./src/container \
    && mkdir -p ./src/page \
    && mkdir -p ./src/store

RUN mkdir -p ./public

COPY package.json .

CMD tail -f /dev/null
