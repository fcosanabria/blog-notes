FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

# Install dependencies including tmux and clipboard tools for Wayland
RUN apt-get update -y && apt-get install -y --no-install-recommends \
    curl ca-certificates fish git tmux wl-clipboard xclip \
  && rm -rf /var/lib/apt/lists/*

# Adding Installing Mise
COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# make sure mise is activated in bash, zsh, and fish. Might be overridden by a user's dotfiles.
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(mise activate zsh)"' >> /home/vscode/.zshrc

# Create tmux config for clipboard integration
RUN mkdir -p /home/vscode/.config/tmux && \
    chown -R vscode:vscode /home/vscode/.config
