# FROM debian:latest
FROM mcr.microsoft.com/devcontainers/cpp:0-debian-11

LABEL description="Base Image for Pi Pico development"

# Install required packages
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y update && apt-get install -y \
    # Tools
    git \
    wget \
    # Toolchain
    cmake \
    gcc-arm-none-eabi \
    libnewlib-arm-none-eabi \
    build-essential \
    python3 \
    # Picotool
    libusb-1.0-0-dev \
    pkg-config

# Specify the working directory
# WORKDIR /usr/src

# Install the SDK
ENV PICO_ROOT=/usr/src/pico
RUN mkdir -p $PICO_ROOT

# Install Pico-SDK
ENV PICO_SDK_PATH=$PICO_ROOT/pico-sdk
RUN git clone -b master https://github.com/raspberrypi/pico-sdk.git $PICO_SDK_PATH && \
    cd $PICO_SDK_PATH && \
    git submodule update --init
RUN echo "export PICO_SDK_PATH="$PICO_SDK_PATH >> ~/.bashrc

# # Install Pico Examples
# ENV PICO_EXAMPLES_PATH=$PICO_ROOT/pico-examples
# RUN git clone -b master https://github.com/raspberrypi/pico-examples.git $PICO_EXAMPLES_PATH
# RUN echo "export PICO_EXAMPLES_PATH="$PICO_EXAMPLES_PATH >> ~/.bashrc

# # Install Pico Extras
# ENV PICO_EXTRAS_PATH=$PICO_ROOT/pico-extras
# RUN git clone -b master https://github.com/raspberrypi/pico-extras.git $PICO_EXTRAS_PATH
# RUN echo "export PICO_EXTRAS_PATH="$PICO_EXTRAS_PATH >> ~/.bashrc

# # Install Pico Playground
# ENV PICO_PLAYGROUND_PATH=$PICO_ROOT/pico-playground
# RUN git clone -b master https://github.com/raspberrypi/pico-playground.git $PICO_PLAYGROUND_PATH
# RUN echo "export PICO_PLAYGROUND_PATH="$PICO_PLAYGROUND_PATH >> ~/.bashrc

# Install Picotool
ENV PICOTOOL_PATH=$PICO_ROOT/picotool
RUN git clone -b master https://github.com/raspberrypi/picotool.git $PICOTOOL_PATH
RUN cd $PICOTOOL_PATH && \
    mkdir build && \
    cd build && \
    cmake .. && \
    make && \
    cp picotool /usr/local/bin/