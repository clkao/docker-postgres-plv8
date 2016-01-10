FROM postgres:9.4
MAINTAINER Chia-liang Kao <clkao@clkao.org>

RUN apt-get update \
  && apt-get install -y build-essential curl git-core postgresql-server-dev-$PG_MAJOR \
  && rm -rf /var/lib/apt/lists/*

ENV PLV8_COMMIT ca2fa002dafc1d7a229892d8f16b92ab61182a2c

RUN cd /tmp \
  && git clone https://github.com/plv8/plv8.git \
  && cd plv8 \
  && git checkout $PLV8_COMMIT \
  && cd /tmp/plv8 \
  && make static install \
  && rm -rf /tmp/plv8
