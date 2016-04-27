## OpenBLAS docker image

[![](https://imagelayers.io/badge/canesin/openblas-git:latest.svg)](https://imagelayers.io/?images=canesin/openblas-git:latest)

Docker image based on alpine:edge for OpenBLAS git, AVX (SandyBridge) target.
Library is installed at /opt/OpenBLAS/ clang used as compiler

## Usage

Build and start bash in the container:
```bash
$ docker pull canesin/openblas-git
$ docker run --rm -it canesin/openblas-git bash
```
