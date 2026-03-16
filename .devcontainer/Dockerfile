# 1. Base Topology Upgrade
# Utilizing the '1' tag ensures the latest stable Debian kernel is used, 
# mitigating immediate repository archiving issues.
FROM mcr.microsoft.com/devcontainers/miniconda:1

# 2. Resilient Package Acquisition
# The --allow-releaseinfo-change flag acts as a permanent fix against 
# future upstream suite transitions (e.g., stable -> oldstable).
RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update --allow-releaseinfo-change \
    && apt-get -y install --no-install-recommends \
        build-essential \
        cmake \
        gfortran \
        git \
        zsh \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# 3. Environment Variable Injection
# Set Zsh as the default shell to mirror the APFS environment deterministically.
RUN chsh -s $(which zsh) vscode
