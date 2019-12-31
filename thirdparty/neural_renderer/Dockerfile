FROM impersonator/base_dev:1.0

COPY . /impersonator/thirdparty/neural_renderer

RUN apt-get update \
    && apt-get install -y \
        build-essential \
        --no-install-recommends \
    && cd /impersonator/thirdparty/neural_renderer \
    && python setup.py install

		
