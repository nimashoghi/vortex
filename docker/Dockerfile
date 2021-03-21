FROM nvidia/cuda:11.2.2-cudnn8-runtime-ubuntu20.04

RUN apt-get update && apt-get install --yes --no-install-recommends \
    python python3 git build-essential tar wget

WORKDIR /opt
RUN git clone --recursive https://github.com/vortexgpgpu/vortex.git

WORKDIR /opt/vortex
RUN ./ci/toolchain_install.sh -all

ENV RISCV_TOOLCHAIN_PATH=/opt/riscv-gnu-toolchain
ENV VERILATOR_ROOT=/opt/verilator
ENV PATH=$VERILATOR_ROOT/bin:$PATH

RUN make -j
