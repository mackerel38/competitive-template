FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install g++ 12, clang-format, git, zip, python3, pip, and curl
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:ubuntu-toolchain-r/test && \
    apt-get update && \
    apt-get install -y \
    g++-12 \
    clang-format \
    git \
    zip \
    python3 \
    python3-pip \
    curl \
    wget \
    build-essential \
    lsb-release \
    ca-certificates

# Set g++ and gcc version 12 as default
RUN update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-12 100 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 100

# Install Rust
RUN curl https://sh.rustup.rs -sSf | bash -s -- -y
ENV PATH="/root/.cargo/bin:${PATH}"

# Install PyPy (via portable tarball)
RUN curl -L -o pypy.tar.bz2 https://downloads.python.org/pypy/pypy3.9-v7.3.13-linux64.tar.bz2 && \
    tar -xjf pypy.tar.bz2 && \
    mv pypy3.9-v7.3.13-linux64 /opt/pypy && \
    ln -s /opt/pypy/bin/pypy3 /usr/local/bin/pypy3 && \
    rm pypy.tar.bz2
