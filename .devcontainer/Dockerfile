# Base image optimized for Python/C++ scientific computing
FROM mcr.microsoft.com/devcontainers/miniconda:0-3

# Install rigorous build-essential tools for compiled binaries (C++, CMake)
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        build-essential \
        cmake \
        gfortran \
        git \
        zsh \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Set Zsh as the default shell to mirror your local APFS environment
RUN chsh -s $(which zsh) vscode
