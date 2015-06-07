FROM postgres:9.4
MAINTAINER Chia-liang Kao <clkao@clkao.org>

RUN apt-get update \
	&& apt-get install -y build-essential libv8-dev git-core postgresql-server-dev-$PG_MAJOR \
	&& rm -rf /var/lib/apt/lists/*

ENV PLV8_BRANCH r1.4

RUN cd /tmp && git clone -b $PLV8_BRANCH https://github.com/plv8/plv8.git \
  && cd /tmp/plv8 \
  && make all install
