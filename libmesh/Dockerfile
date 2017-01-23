FROM canesin/slepc:latest
MAINTAINER Fabio C. Canesin, fabio.canesin@gmail.com

# User clang as default compiler (this is redudant from canesin/slepc
# but I repeat this here for explicity)
ENV CC clang
ENV CXX clang++
ENV PETSC_DIR /opt/petsc
ENV SLEPC_DIR /opt/slepc

# Compile LibMesh with latest clang
RUN apk add --no-cache curl build-base clang cmake && \
    cd /tmp/ && \
    curl -L https://github.com/libmesh/libmesh/archive/master.tar.gz | tar xz && \
    cd `ls | grep libmesh` && \
    ./configure --prefix=/opt/libmesh \
        --with-methods="opt dbg" \
        --with-metis=PETSc \
        --enable-exodus \
        --enable-ifem \
        --enable-cxx11 \
        --enable-perflog \
        --enable-silent-rules \
        --enable-unique-ptr \
        --enable-unique-id \
        --disable-fortran \
        --disable-pthreads \
        --disable-maintainer-mode && \
    make && make install && \
    make installcheck && \
    apk del curl build-base clang cmake && \
    rm -rf /usr/share/man/* /tmp/* /var/cache/apk/*

# Setup LibMesh location
ENV LIBMESH_DIR /opt/libmesh
