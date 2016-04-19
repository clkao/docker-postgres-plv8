FROM postgres:9.4

MAINTAINER Chia-liang Kao <clkao@clkao.org>

ENV PLV8_VERSION=v1.4.7 \
    PLV8_SHASUM="bd5802a9714f8380fefa0d2bd68687ab0dc9d1b01a83309e965a346a6766777c  v1.4.7.tar.gz"

RUN buildDependencies="build-essential \
    ca-certificates \
    curl \
    git-core \
    libv8-dev \
    postgresql-server-dev-$PG_MAJOR" \
    runtimeDependencies="libv8-3.14.5" \
  && apt-get update \
  && apt-get install -y --no-install-recommends ${buildDependencies} \
  && mkdir -p /tmp/build \
  && curl -o /tmp/build/${PLV8_VERSION}.tar.gz -SL "https://github.com/plv8/plv8/archive/$PLV8_VERSION.tar.gz" \
  && cd /tmp/build \
  && echo ${PLV8_SHASUM} | sha256sum -c \
  && tar -xzf /tmp/build/${PLV8_VERSION}.tar.gz -C /tmp/build/ \
  && cd /tmp/build/plv8-${PLV8_VERSION#?} \
  && make all install \
  && strip /usr/lib/postgresql/${PG_MAJOR}/lib/plv8.so \
  && cd / \
  && apt-get install ${runtimeDependencies} \
  && apt-get clean \
  && apt-get remove -y  ${buildDependencies} \
  && apt-get autoremove -y \
  && rm -rf /tmp/build /var/lib/apt/lists/*
