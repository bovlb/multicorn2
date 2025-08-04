FROM mcr.microsoft.com/devcontainers/python:3.11

RUN apt-get update && apt-get install -y python3.11-dev

RUN echo "deb [signed-by=/usr/share/keyrings/postgresql-archive-keyring.gpg] http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" \
  | tee /etc/apt/sources.list.d/pgdg.list && \
  curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor \
  | tee /usr/share/keyrings/postgresql-archive-keyring.gpg > /dev/null && \
  apt-get update
  
# Install PostgreSQL
ARG POSTGRES_VERSION=17
RUN apt-get update && apt-get install -y \
    postgresql-${POSTGRES_VERSION} \
    postgresql-server-dev-${POSTGRES_VERSION} \
    postgresql-contrib \
    libpq-dev \``
    build-essential \
    git \
    && rm -rf /var/lib/apt/lists/*

# Optional: pre-create a multicorn workspace directory
RUN mkdir -p /workspaces/multicorn2
WORKDIR /workspaces/multicorn2

# Install nix for tests
RUN curl -L https://nixos.org/nix/install | sh -s -- --no-daemon
RUN mkdir -p ~/.config/nix && echo "experimental-features = nix-command flakes" >> ~/.config/nix/nix.conf
RUN . /home/vscode/.nix-profile/etc/profile.d/nix.sh