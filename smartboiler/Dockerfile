# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

WORKDIR /usr/src

COPY requirements.txt /usr/src/requirements.txt

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        python3 \
        python3-pip \
        python3-dev \
        build-essential \
        git \
    && pip3 install --no-cache-dir -r requirements.txt \
    && apt-get purge -y --auto-remove \
        python3-dev \
        build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /
# Copy root filesystem
COPY rootfs /
