## PETSc docker image

[![](https://imagelayers.io/badge/canesin/petsc:latest.svg)](https://imagelayers.io/?images=canesin/petsc:latest)

Install at /opt/petsc , it is built from on canesin/openblas using clang as compiler.

- PETSc latest stable (3.7.x), AVX2 optimized
- OpenBLAS develop, AVX2 optimized
- MPICH 3.1.x
- METIS 5.1.x
- ParMETIS 4.0.x
- HYPRE 2.10.x
- SuperLU_dist 4.x

## Usage

Build and start bash in the container:
```bash
$ docker pull canesin/petsc
$ docker run --rm -it canesin/petsc bash
```

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