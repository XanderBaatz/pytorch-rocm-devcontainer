FROM rocm/pytorch:latest

ENV DEBIAN_FRONTEND=noninteractive
ENV HSA_OVERRIDE_GFX_VERSION=11.5.0
#ENV CUPY_INSTALL_USE_HIP=1
ENV ROCM_HOME=/opt/rocm
ENV HCC_AMDGPU_TARGET=gfx1151
ENV PYTORCH_ROCM_ARCH=gfx1151

#RUN apt update -y && \
#    apt autoremove -y && \
#    apt install -y gnupg \
#    g++ \
#    python3-dev \
#    python3-pip \
#    rocm-dev \
#    rocm-libs \
#    build-essential && \
#    apt-get clean && \
#    rm -rf /var/lib/apt/lists/*

RUN apt update && \
    apt install --no-install-recommends -y build-essential gcc && \
    apt clean && rm -rf /var/lib/apt/lists/*

#RUN chsh -s /bin/bash jenkins

# Set environment for CC, else CuPy wouldn't build wheel (g++ error)
#ENV CC=hipcc
#ENV CXX=hipcc

COPY requirements.txt /tmp/requirements.txt

RUN pip install --no-cache-dir -r /tmp/requirements.txt
