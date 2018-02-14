FROM postgres:9.4

MAINTAINER Chia-liang Kao <clkao@clkao.org>

ENV PLV8_VERSION=v2.1.0 \
    PLV8_SHASUM="207d712e919ab666936f42b29ff3eae413736b70745f5bfeb2d0910f0c017a5c  v2.1.0.tar.gz"

RUN buildDependencies="build-essential \
    ca-certificates \
    curl \
    git-core \
    postgresql-server-dev-$PG_MAJOR" \
  && apt-get update \
  && apt-get install -y --no-install-recommends ${buildDependencies} \
  && mkdir -p /tmp/build \
  && curl -o /tmp/build/${PLV8_VERSION}.tar.gz -SL "https://github.com/plv8/plv8/archive/$PLV8_VERSION.tar.gz" \
  && cd /tmp/build \
  && echo ${PLV8_SHASUM} | sha256sum -c \
  && tar -xzf /tmp/build/${PLV8_VERSION}.tar.gz -C /tmp/build/ \
  && cd /tmp/build/plv8-${PLV8_VERSION#?} \
  && make static \
  && make install \
  && strip /usr/lib/postgresql/${PG_MAJOR}/lib/plv8.so \
  && cd / \
  && apt-get clean \
  && apt-get remove -y  ${buildDependencies} \
  && apt-get autoremove -y \
  && rm -rf /tmp/build /var/lib/apt/lists/*
