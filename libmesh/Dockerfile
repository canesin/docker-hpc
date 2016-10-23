FROM canesin/slepc:latest
MAINTAINER Fabio C. Canesin, fabio.canesin@gmail.com

# User clang as default compiler (this is redudant from canesin/slepc
# but I repeat this here for explicity)
ENV CC clang
ENV CXX clang++
ENV PETSC_DIR /opt/petsc
ENV SLEPC_DIR /opt/slepc

# Compile LibMesh with latest clang
RUN apk add --no-cache curl build-base clang unzip && \
    curl -o /tmp/libmesh.zip -sSL https://github.com/libMesh/libmesh/archive/master.zip && \
    cd /tmp/ && \
    unzip libmesh.zip && \
    cd `ls | grep libmesh` && \
    ./configure --with-methods="opt dbg" \
                --prefix=/opt/libmesh \
                --with-metis=PETSc \
                --enable-ifem \
                --enable-cxx11 \
                --enable-silent-rules \
                --enable-unique-ptr \
                --enable-unique-id \
                --disable-warnings \
                --disable-timestamps \
                --disable-fortran \
                --disable-pthreads \
                --disable-openmp \
                --disable-maintainer-mode && \
    make -j$(nproc) && \
    make install -j$(nproc) && \
    make installcheck -j$(nproc) METHODS=opt && \
    apk del curl build-base clang unzip && \
    rm -rf /usr/share/man/* /tmp/* /var/cache/apk/*

# Setup LibMesh location
ENV LIBMESH_DIR /opt/libmesh
