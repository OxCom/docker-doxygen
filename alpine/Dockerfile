FROM alpine

ARG DOXYGEN_RELEASE_TAG=Release_1_8_17
ENV TERM=xterm \
    DOXYGEN_RELEASE_TAG=${DOXYGEN_RELEASE_TAG} \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    LC_CTYPE=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8

RUN apk update \
    && apk upgrade \
    && apk add build-base \
         git openssh \
         flex \
         bison \
         cmake \
         texmf-dist texlive \
         python3 \
    && mkdir -p /tmp/project/bin \
    && cd /tmp/project/ \
    && git clone --branch ${DOXYGEN_RELEASE_TAG} --depth 1 https://github.com/doxygen/doxygen.git doxygen \
    && mkdir -p /tmp/project/doxygen/build \
    && cd /tmp/project/doxygen/build \
    && cmake -G "Unix Makefiles" .. \
    && make install \
    && doxygen --help \
    && apk del build-base \
    && rm -rf /tmp/* /var/cache/apk/*

CMD ["doxygen", "--help"]
