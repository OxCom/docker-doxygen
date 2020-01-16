FROM centos:8

ARG RELEASE_TAG=Release_1_8_17
ENV RELEASE_TAG=${RELEASE_TAG}

RUN yum -y update \
    && yum group install -y "Development Tools" \
    && yum install -y git openssl \
        flex bison make cmake \
        python3 \
        texlive texlive-*.noarch \
        unzip \
    && mkdir -p /tmp/project/bin \
    && cd /tmp/project/ \
    && git clone --branch ${RELEASE_TAG} --depth 1 https://github.com/doxygen/doxygen.git doxygen \
    && mkdir -p /tmp/project/doxygen/build \
    && cd /tmp/project/doxygen/build \
    && cmake -G "Unix Makefiles" .. \
    && make install \
    && doxygen --help \
    && yum group remove -y "Development Tools" \
    && yum clean all \
    && rm -rf /tmp/*

CMD ["doxygen", "--help"]
