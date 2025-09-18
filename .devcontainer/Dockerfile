FROM mcr.microsoft.com/devcontainers/base:jammy

ARG PIXI_VERSION=v0.55.0

# Install Pixi
RUN curl -L -o /usr/local/bin/pixi -fsSL --compressed "https://github.com/prefix-dev/pixi/releases/download/${PIXI_VERSION}/pixi-$(uname -m)-unknown-linux-musl" && \
    chmod +x /usr/local/bin/pixi && \
    pixi info

ENV PATH="/root/.pixi/bin:$PATH"

# Install Astral uv
RUN pixi global install uv

# Set up user environment for Codespaces/VSCode
USER vscode
WORKDIR /workspaces/${GIT_REPO_NAME}

RUN echo 'eval \"$(pixi completion -s bash)\"' >> /home/vscode/.bashrc
