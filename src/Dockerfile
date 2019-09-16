ARG BASE
ARG TAG

FROM ${BASE}:${TAG}

LABEL maintainer="szymonmaszke <szymon.maszke@protonmail.com>"

WORKDIR /opt/torchstar

COPY . .

RUN apt-get update && apt-get install -y --no-install-recommends \
      ca-certificates \
      python3.7 \
      python3-distutils \
      curl && \
      rm -rf /var/lib/apt/lists/* && \
      curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && \
      ln -s python3.7 python && \
      python3.7 get-pip.py && \
      rm get-pip.py && \
      pip install --upgrade pip -v setuptools wheel && \
      torchstar-docker/src/install_torch ${BASE} && \
      rm -rf *

WORKDIR /home
