# vim:set ft=dockerfile:

FROM postgres

RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list

RUN apt-get update && apt-get install -y \
    postgresql-11-postgis-2.5 \
    rsync \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN apt-get update \
 && apt-get install -y wget \
    libboost-graph-dev \
    cmake \
    libcgal-dev \
    libperl-dev \
    g++ \
    postgresql-server-dev-11 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
 && mkdir /build_pgrouting

WORKDIR /build_pgrouting

RUN wget https://github.com/pgRouting/pgrouting/releases/download/v2.6.2/pgrouting-2.6.2.tar.gz && tar xzf pgrouting-2.6.2.tar.gz

WORKDIR pgrouting-2.6.2

RUN mkdir build

WORKDIR build

RUN cmake ..\
 && make \
 && make install

WORKDIR /

RUN rm -rf /build_pgrouting

RUN apt-get update \
 && apt-get install -y osm2pgsql \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*