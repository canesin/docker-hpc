FROM alpine:edge
MAINTAINER Fabio C. Canesin, fabio.canesin@gmail.com

# User clang as default compiler
ENV CC clang
ENV CXX clang++

# Compile openblas with latest clang
RUN apk add --no-cache curl unzip build-base gfortran clang perl linux-headers && \
    curl -o /tmp/openblas.zip -sSL https://github.com/xianyi/OpenBLAS/archive/develop.zip && \
    mkdir -p /etc/ld.so.conf.d/ && \
    echo "/opt/OpenBLAS/lib" > /etc/ld.so.conf.d/openblas.conf && \
    cd /tmp/ && \
    unzip openblas.zip && \
    cd `ls | grep OpenBLAS` && \
    make TARGET=HASWELL NO_AFFINITY=1 NUM_THREADS=1 && \
    make install && \
    apk del curl unzip build-base gfortran clang perl linux-headers && \
    rm -rf /usr/share/man/* /tmp/* /var/cache/apk/*
