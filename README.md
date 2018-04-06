# mountainR
Bringing R and alpine to docker

## Overview

This repository contains Dockerfiles for different Docker containers with [R](https://www.r-project.org/) based on [alpine](https://alpinelinux.org/). For most use cases, the Docker collection of [rocker](https://github.com/rocker-org/rocker) offers more convenient and complete installations.

## Why?

Alpine is a minimal and secure linux distribution based on the [musl C library](https://www.musl-libc.org/) and the [Busybox utilities](https://www.busybox.net/about.html). Although other linux distros are far better suited for working with R, a minimal and secure setup can be preferable when memory is limited and R dockers are deployed in a wider toolchain. The core Alpine docker image is only 5 Mb.

These Docker containers are primarily developed to be used inside an online course system used at Ghent University. 

## Important notes

To keep every layer minimal, the tools needed for installing the different components are removed again after installation for as far as they're not needed for the functioning of the installed R toolset. This also means that you almost always need to tailor the provided containers to your own needs.

 - In order to install R packages, one needs to install the alpine packages `R-dev` and `R-doc`. This can be done using `apk` as explained in the [alpine linux wiki](https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management)
 
 ```
 apk update
 apk add R-dev R-doc
 ```

 - To install packages with code that needs compiling, the extra alpine packages `libc-dev` and possibly `g++` are needed on top of `R-dev`. 
 
 - As on debian, the latest R version is not available in the package repo of the stable Alpine release. This means that stable versions likely have an older R version installed.
