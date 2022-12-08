ARG VARIANT=16
FROM mcr.microsoft.com/vscode/devcontainers/typescript-node:${VARIANT}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends fzf silversearcher-ag \
    && apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/*

ARG VUE_CLI_VERSION
RUN su node -c "umask 0002 && npm install -g @vue/cli@${VUE_CLI_VERSION} http-server yrm"

ENV SHELL /bin/zsh
ARG HTTP_PROXY
ARG HTTPS_PROXY

RUN export https_proxy=$HTTPS_PROXY && wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O - | zsh || true

RUN export https_proxy=$HTTPS_PROXY && git clone --depth=1 https://github.com/romkatv/powerlevel10k.git /home/node/.oh-my-zsh/custom/themes/powerlevel10k \
    && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git /home/node/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting \
    && git clone https://github.com/zsh-users/zsh-autosuggestions.git /home/node/.oh-my-zsh/custom/plugins/zsh-autosuggestions \
    && git clone https://github.com/zsh-users/zsh-completions.git /home/node/.oh-my-zsh/custom/plugins/zsh-completions \
    && git clone https://github.com/supercrabtree/k.git /home/node/.oh-my-zsh/custom/plugins/k

ADD --chown=node /.devcontainer/.zshrc /home/node

EXPOSE 5173