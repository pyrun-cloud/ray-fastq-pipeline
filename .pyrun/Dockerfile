FROM public.ecr.aws/docker/library/python:3.10-slim-buster

ARG FUNCTION_DIR="/function"
ARG LITHOPS

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      git \
      wget \
      gcc \
      make \
      zlib1g-dev && \
    rm -rf /var/lib/apt/lists/*

RUN wget -q https://raw.githubusercontent.com/circulosmeos/gztool/master/gztool.c -O /tmp/gztool.c && \
    gcc -O3 -o /usr/local/bin/gztool /tmp/gztool.c -lz -lm && \
    chmod +x /usr/local/bin/gztool && \
    rm /tmp/gztool.c

RUN pip install --no-cache-dir \
      ipykernel \
      ipywidgets \
      "$LITHOPS" \
      ray \
      scikit-learn \
      cloud-dataplug \
      cloud-data-cockpit

WORKDIR ${FUNCTION_DIR}

