FROM postgres:9.4
MAINTAINER Chia-liang Kao <clkao@clkao.org>

ENV PLV8_MAJOR 1.4

RUN apt-get update \
	&& apt-get install -y build-essential libv8-dev git-core postgresql-server-dev-$PG_MAJOR \
	&& rm -rf /var/lib/apt/lists/*

RUN cd /tmp && git clone -b r$PLV8_MAJOR https://github.com/clkao/plv8js.git \
  && cd /tmp/plv8js \
  && make all install
