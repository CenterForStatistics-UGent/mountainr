## alpine-r-core

This docker image contains a core R installation of the latest R in the edge branch. 
It doesn't contain the documentation or the necessary alpine packages to install R packages
from source. If you want to build on `alpine-r-core` you need the following in the docker file:

```
 RUN apk add R-dev@edge R-doc@edge --no-cache
 ```
 
 ### NOTE
 
 To install packages with code that needs compiling, the extra alpine packages `libc-dev` and possibly `g++` are needed on top of `R-dev`. 
 See also this [issue](https://bugs.alpinelinux.org/issues/8770).