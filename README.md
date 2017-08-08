# Dockerfiles for IoT Devkit

[![Build Status](https://travis-ci.org/dnoliver/iot-devkit-docker.svg?branch=master)](https://travis-ci.org/dnoliver/iot-devkit-docker)

## Docker Images Hierarchy for Mraa

To improve build times and images sizes, mraa use a build hierarchy to incrementally
create a build environment. Find below a brief description of them:

** mraa-base **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-base.svg)](https://microbadger.com/images/dnoliver/mraa-base "mraa-base")

Provides the basic infrastructure and tools to compile C/C++ code and documentation.

** mraa-python **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-python.svg)](https://microbadger.com/images/dnoliver/mraa-python "mraa-python")

Provides the python2/python3 build tools. Depends on `mraa-base`.

** mraa-java **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-java.svg)](https://microbadger.com/images/dnoliver/mraa-java "mraa-java")

Provides the Java build tools. Depends on `mraa-base`.

** mraa-android **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-android.svg)](https://microbadger.com/images/dnoliver/mraa-android "mraa-android")

 rovides the Android Things build tools.  Depends on `mraa-base`.

** mraa-node4 **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-node4.svg)](https://microbadger.com/images/dnoliver/mraa-node4 "mraa-node4")

Provides the Node.js v4.4.7 build tools. Depends on `mraa-base`.

** mraa-node5 **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-node5.svg)](https://microbadger.com/images/dnoliver/mraa-node5 "mraa-node5")

Same as `mraa-node4`, but using Node.js v5.12.0.

** mraa-node6 **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-node6.svg)](https://microbadger.com/images/dnoliver/mraa-node6 "mraa-node6")

Same as `mraa-node4`, but using Node.js v6.11.0.

** mraa-all **

[![](https://images.microbadger.com/badges/image/dnoliver/mraa-all.svg)](https://microbadger.com/images/dnoliver/mraa-all "mraa-all")

Provides python, java, and node build tools and additional tools . Depends on `mraa-base`.

## Docker Images Hierarchy for Upm

To improve build times and images sizes, upm use a build hierarchy to incrementally
create a build environment. Find below a brief description of them:

** upm-base**

[![](https://images.microbadger.com/badges/image/dnoliver/upm-base.svg)](https://microbadger.com/images/dnoliver/upm-base "upm-base")

Provides the basic infrastructure and tools to compile C/C++ code and documentation.

** upm-python **

[![](https://images.microbadger.com/badges/image/dnoliver/upm-python.svg)](https://microbadger.com/images/dnoliver/upm-python "upm-python")

Provides the python2/python3 build tools. Depends on `upm-base`.

** upm-java **

[![](https://images.microbadger.com/badges/image/dnoliver/upm-java.svg)](https://microbadger.com/images/dnoliver/upm-java "upm-java")

Provides the Java build tools. Depends on `upm-base`.

** upm-android **

[![](https://images.microbadger.com/badges/image/dnoliver/upm-android.svg)](https://microbadger.com/images/dnoliver/upm-android "upm-android")

Provides the Android Things build tools. Depends on `upm-java`.

** upm-node4 **

[![](https://images.microbadger.com/badges/image/dnoliver/upm-node4.svg)](https://microbadger.com/images/dnoliver/upm-node4 "upm-node4")

Provides the Node.js v4.4.7 build tools. Depends on `upm-base`.

** upm-node5 **

[![](https://images.microbadger.com/badges/image/dnoliver/upm-node5.svg)](https://microbadger.com/images/dnoliver/upm-node5 "upm-node5")

Same as `upm-node4`, but using Node.js v5.12.0.

** upm-node6 **

[![](https://images.microbadger.com/badges/image/dnoliver/upm-node6.svg)](https://microbadger.com/images/dnoliver/upm-node6 "upm-node6")

Same as `upm-node4`, but using Node.js v6.11.0.

** upm-all **

[![](https://images.microbadger.com/badges/image/dnoliver/upm-all.svg)](https://microbadger.com/images/dnoliver/upm-all "upm-all")

# Proxy Consideration

**docker build fails to fetch packages from internet**

docker-compose will automatically take `http_proxy`, `https_proxy`, and `no_proxy`
environment variables and use it as build arguments. Be sure to properly configure
this variables before building.

docker, unlinke docker-compose, do not take the proxy settings from the environment
automatically. You need to send them as build arguments:

```sh
# From the repository root folder
$ docker build \
    -d docker/Dockerfile.base \
    --build-arg http_proxy=$http_proxy \
    --build-arg https_proxy=$https_proxy \
    --build-arg no_proxy=$no_proxy \
    -t mraa-base .
```
