FROM ubuntu:trusty

RUN apt-get update \
  && apt-get install --no-install-recommends -y \
      ca-certificates iproute2 git lsb-release python-pip \
  && apt-get autoremove  \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*cache.bin

RUN git clone --branch master --depth=1 \
  https://github.com/openstack-dev/devstack

RUN apt-get update \
  && cd devstack \
  && tools/install_prereqs.sh \
  && apt-get autoremove  \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*cache.bin

RUN pip install -U pip \
  && pip install virtualenv \
  && virtualenv /venv
