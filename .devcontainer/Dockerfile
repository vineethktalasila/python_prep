# 1. Base Topology Fix
# Reverting to the valid major version tree. Using '0-bookworm' maps 
# directly to Debian 12, ensuring a modern kernel for scientific compute.
FROM mcr.microsoft.com/devcontainers/miniconda:0-bookworm

# 2. Resilient Package Acquisition
# The --allow-releaseinfo-change flag mathematically bypasses the upstream 
# Debian suite transition that caused your original Exit 100 error.
RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update --allow-releaseinfo-change \
    && apt-get -y install --no-install-recommends \
        build-essential \
        cmake \
        gfortran \
        git \
        zsh \
        ccache \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# 3. C++ Compilation Optimization
# Prepend ccache to the path so gcc/g++ invocations are automatically cached
ENV PATH="/usr/lib/ccache:${PATH}"

# 4. Environment Variable Injection
# Set Zsh as the default shell to mirror the APFS environment deterministically.
RUN chsh -s $(which zsh) vscode
