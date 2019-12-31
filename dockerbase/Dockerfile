FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu16.04
COPY requirements.txt /pip_requirements/
COPY ./sources.list /etc/apt/

RUN rm -rf /var/lib/apt/lists/* \
    && apt-get clean \
    && apt-get update \
    && apt-get install -y software-properties-common --no-install-recommends\
    && add-apt-repository -y ppa:deadsnakes/ppa \
    && apt-get update \
    && apt-get install -y \
        python3.6 \
        libsndfile1 \
        python3.6-dev \
        ffmpeg \
        python3-pip \
        libsm6 libxext6 libxrender-dev \
        --no-install-recommends \
    && ln -s /usr/bin/python3.6 /usr/bin/python \
    && ln -s /usr/bin/pip3 /usr/bin/pip \
    && python -m pip --no-cache-dir install -i https://repo.huaweicloud.com/repository/pypi/simple -U pip setuptools \
    && python -m pip --no-cache-dir install -i https://repo.huaweicloud.com/repository/pypi/simple -r /pip_requirements/requirements.txt