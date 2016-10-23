FROM canesin/openblas:latest
MAINTAINER Fabio C. Canesin, fabio.canesin@gmail.com

# User clang as default compiler (this is redudant from canesin/openblas
# but I repeat this here for explicity)
ENV CC clang
ENV CXX clang++

# Compile PETSc with latest clang
RUN apk add --no-cache curl build-base gfortran clang perl cmake python linux-headers && \
    curl -o /tmp/petsc.tar.gz -sSL http://ftp.mcs.anl.gov/pub/petsc/release-snapshots/petsc-lite-3.7.tar.gz && \
    cd /tmp/ && \
    tar xzf petsc.tar.gz && \
    cd `ls | grep petsc` && \
    ./configure PETSC_ARCH=dorcker-opt \
            CC=$CC \
            CXX=$CXX \
            --prefix=/opt/petsc \
            --with-blas-lapack-dir=/opt/OpenBLAS/ \
            --download-mpich \
            --download-superlu_dist \
            --download-metis \
            --download-parmetis \
            --download-hypre \
            --with-debugging=0 \
            COPTFLAGS='-O2 -march=ivybridge -mtune=ivybridge' \
            CXXOPTFLAGS='-O2 -march=ivybridge -mtune=ivybridge' \
            FOPTFLAGS='-O2 -march=ivybridge -mtune=ivybridge' && \
    make && \
    make install && \
    echo "export PETSC_DIR=/opt/petsc" >> $HOME/.bashrc && \
    source $HOME/.bashrc && \
    apk del curl build-base gfortran clang perl cmake python linux-headers && \
    rm -rf /usr/share/man/* /tmp/* /var/cache/apk/*
