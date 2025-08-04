FROM postgres:17-bookworm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    curl \
    sudo \
    git \
    bash \
    locales \
    python3 python3-pip python3-venv python3-setuptools \
    build-essential \
    libpq-dev \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Configure locale
RUN locale-gen en_US.UTF-8
ENV LANG=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8

# Install Nix
RUN curl -L https://nixos.org/nix/install | bash -s -- --no-daemon || true
ENV PATH="/root/.nix-profile/bin:/nix/var/nix/profiles/default/bin:$PATH"