FROM postgres:11.4

LABEL Author="Sebastian Koenig <sebastian.m.koenig@googlemail.com>"

ENV PLV8_VERSION='2.3.12' \
    PLV8_SHASUM='0bd5cbd8e6123d14451780240972289dcf53cf8c1ffa227aa9f34c296cd641d8'
    
RUN tmpBuildDependencies="build-essential \
    ca-certificates \
    curl \
    git-core \
    python \
    gpp \
    cpp \
    pkg-config \
    apt-transport-https \
    cmake \
    postgresql-server-dev-$PG_MAJOR" \ 
    && buildDependencies="libc++-dev" \
    && apt-get update \
    && apt-get install -y --no-install-recommends ${tmpBuildDependencies} \
    && apt-get install -y --no-install-recommends ${buildDependencies} \
    && mkdir -p /tmp/build \
    && curl -o /tmp/build/v$PLV8_VERSION.tar.gz -SL "https://github.com/plv8/plv8/archive/v${PLV8_VERSION}.tar.gz" \ 
    && cd /tmp/build \
    && echo $PLV8_SHASUM v$PLV8_VERSION.tar.gz | sha256sum -c \
    && tar -xzf /tmp/build/v$PLV8_VERSION.tar.gz -C /tmp/build/ \ 
    && cd /tmp/build/plv8-$PLV8_VERSION \
    && make static \
    && make install \
    && strip /usr/lib/postgresql/${PG_MAJOR}/lib/plv8-${PLV8_VERSION}.so \
    && cd / \
    && apt-get clean \
    && apt-get remove -y ${tmpBuildDependencies} \
    && apt-get autoremove -y \
    && rm -rf /tmp/build /var/lib/apt/lists/*