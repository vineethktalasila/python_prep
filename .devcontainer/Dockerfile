# 1. Base Topology Upgrade
# Extracting from the registry manifest, '1-3' maps to Major Version 1, Python 3.
# This modernizes the underlying OS layer, naturally resolving deprecated index errors.
FROM mcr.microsoft.com/devcontainers/miniconda:1-3

# 2. Resilient Package Acquisition
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
# Set Zsh as the default shell to mirror your APFS environment deterministically.
RUN chsh -s $(which zsh) vscode

# Prepend ccache to the path so gcc/g++ invocations are automatically cached
ENV PATH="/usr/lib/ccache:${PATH}"
