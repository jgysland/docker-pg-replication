FROM postgres:9.6-alpine

RUN apk add --virtual build-deps build-base gcc wget git \
 && git clone https://github.com/eulerto/wal2json.git \
 && cd wal2json \
 && USE_PGXS=1 make \
 && USE_PGXS=1 make install \
 && apk del build-deps

COPY ./setup-master.sh /docker-entrypoint-initdb.d/setup-master.sh

RUN chmod 0666 /docker-entrypoint-initdb.d/setup-master.sh
