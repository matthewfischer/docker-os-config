FROM ubuntu:xenial

RUN apt-get update \
  && apt-get install --no-install-recommends -y \
      ca-certificates iproute2 git lsb-release \
  && apt-get autoremove  \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*cache.bin

RUN git clone --branch master --depth=1 \
  https://github.com/openstack-dev/devstack

RUN ln /usr/bin/env /usr/bin/sudo 

RUN apt-get update \
  && cd devstack \
  && tools/install_prereqs.sh \
  && apt-get autoremove  \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*cache.bin
