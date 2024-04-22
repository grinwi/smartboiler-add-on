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
# Setup
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    #     libffi-dev \
        python3 \
        python3-pip \
        python3-dev \
        git \
        build-essential \
    #     coinor-libcbc-dev \
    #     coinor-cbc \
    #     libglpk-dev \
    #     glpk-utils \
    #     libhdf5-dev \
    #     libhdf5-serial-dev \
    #     pkg-config \
    #     python3-h5py \
    #     gfortran \
    #     libatlas-base-dev \
    # && ln -s /usr/include/hdf5/serial /usr/include/hdf5/include \
    # && export HDF5_DIR=/usr/include/hdf5 \
    # && pip3 install --extra-index-url=https://www.piwheels.org/simple --no-cache-dir -U setuptools wheel \
    && pip3 install --extra-index-url=https://www.piwheels.org/simple --no-cache-dir -r requirements.txt \
    && apt-get purge -y --auto-remove \
        python3-pip \
        python3-dev \
        git \
        build-essential \
    #     libhdf5-dev \
    #     libhdf5-serial-dev \
    #     netcdf-bin \
    #     libnetcdf-dev \
    #     pkg-config \
    #     gfortran \
    # && rm -rf /var/lib/apt/lists/*

COPY model_zuka.keras /app/
COPY scaler_zuka.pkl /app/

COPY model_form.keras /app/
COPY scaler_form.pkl /app/

WORKDIR /
# Copy root filesystem
COPY rootfs /

