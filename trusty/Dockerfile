FROM ubuntu:trusty

RUN apt-get update \
  && apt-get install --no-install-recommends -y ca-certificates wget \
  && apt-get autoremove  \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*cache.bin

RUN wget -O devstack.pkglist https://raw.githubusercontent.com/openstack-dev/devstack/master/files/debs/general \
  && perl -pe 's!\#.*!!g' devstack.pkglist > devstack.pkglist.nocomments

RUN apt-get update \
  && apt-get install --no-install-recommends -y $(cat devstack.pkglist.nocomments) \
  && apt-get autoremove  \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*cache.bin
