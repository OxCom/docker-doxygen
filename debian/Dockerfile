FROM debian:stable-slim

ARG DOXYGEN_RELEASE_TAG=Release_1_8_17
ENV TERM=xterm \
    DOXYGEN_RELEASE_TAG=${DOXYGEN_RELEASE_TAG} \
    DEBIAN_FRONTEND=noninteractive \
    INITRD=No \
    LANG=en_US.utf8

RUN apt-get update \
    && apt-get install git flex bison ca-certificates cmake build-essential python -y --no-install-recommends \
    && mkdir -p /tmp/project/bin \
    && cd /tmp/project/ \
    && git clone --branch ${DOXYGEN_RELEASE_TAG} --depth 1 https://github.com/doxygen/doxygen.git doxygen \
    && mkdir -p /tmp/project/doxygen/build \
    && cd /tmp/project/doxygen/build \
    && cmake -G "Unix Makefiles" .. \
    && make install \
    && doxygen --help \
    && apt-get purge -y cmake build-essential git \
    && rm -rf /tmp/* /var/tmp/* \
              /var/lib/apt/lists/* \
              /var/cache/apt/archives/*.deb \
              /var/cache/apt/archives/partial/*.deb \
              /var/cache/apt/*.bin

CMD ["doxygen", "--help"]
