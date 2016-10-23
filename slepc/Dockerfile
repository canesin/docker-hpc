FROM canesin/petsc:latest
MAINTAINER Fabio C. Canesin, fabio.canesin@gmail.com

# User clang as default compiler (this is redudant from canesin/openblas
# but I repeat this here for explicity)
ENV CC clang
ENV CXX clang++

# Compile SLEPc with latest clang
RUN apk add --no-cache curl build-base clang perl cmake && \
    curl -o /tmp/slepc.tar.gz -sSL https://bitbucket.org/slepc/slepc/get/maint.tar.gz && \
    cd /tmp/ && \
    tar xzf slepc.tar.gz && \
    cd `ls | grep slepc` && \
    ./configure --prefix=/opt/slepc && \
    make
    make install && \
    echo "export SLEPC_DIR=/opt/slepc" >> $HOME/.bashrc && \
    source $HOME/.bashrc && \
    apk del curl build-base clang perl cmake && \
    rm -rf /usr/share/man/* /tmp/* /var/cache/apk/*
