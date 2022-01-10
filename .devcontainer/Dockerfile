# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.195.0/containers/php/.devcontainer/base.Dockerfile
# [Choice] PHP version (use -bullseye variants on local arm64/Apple Silicon): 8-apache-bullseye, 8.1-apache-bullseye, 8.0-apache-bullseye, 7-apache-bullseye, 7.4-apache-bullseye, 8-apache-buster, 8.1-apache-buster, 8.0-apache-buster, 7-apache-buster, 7.4-apache-buster
ARG VARIANT="8.1-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/php:0-${VARIANT}

# [Choice] Node.js version: none, lts/*, 16, 14, 12, 10
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] Uncomment this section to install additional OS packages.
RUN curl -sSLf \
        -o /usr/local/bin/install-php-extensions \
        https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions zip sodium xsl soap sockets pdo_mysql intl bcmath gd xmlrpc && \
    mv /usr/local/etc/php/conf.d/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini.disable

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1