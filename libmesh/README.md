## LibMesh docker image

[![](https://imagelayers.io/badge/canesin/libmesh:latest.svg)](https://imagelayers.io/?images=canesin/libmesh:latest)

Install at /opt/libmesh , it is built from on canesin/slepc using clang as compiler.

- LibMesh from git master
- SLEPc 3.7.x
- PETSc 3.7.x, AVX optimized
    - MPICH
    - METIS
    - ParMETIS
    - HYPRE
    - SuperLU_dist
- OpenBLAS develop, AVX optimized

```bash
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
            --disable-maintainer-mode
```

## Usage

To get a copy of the image and start bash in it:
```bash
$ docker pull canesin/libmesh
$ docker run -rm -it canesin/libmesh bash
```

You will probably want to mount a local machine folder and start bash on it. To do so you can proceed by setting a mySRC environment variable to your project and executing the following commands:
```bash
$ export mySRC="PATH_TO_YOUR_PROJECT_FILES"
$ export LIBMESH_IMG="canesin/libmesh"
$ alias src="docker run --rm -itv ${mySRC}:/opt/src ${LIBMESH_IMG} /bin/sh -c 'cd /opt/src; exec bash'"
```
Now just type "src".
To permanently have the src command add the lines above to ~/.bashrc or your equivalent.
You can use this bash session as a build machine, develop normally with your text editor in your current OS and local file system.

## License

The MIT License (MIT)

Copyright (c) 2016 Fábio César Canesin <fabio.canesin@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
