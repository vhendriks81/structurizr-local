# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.145.1/containers/java/.devcontainer/base.Dockerfile

# [Choice] Java version: 11, 15
ARG VARIANT="15"
FROM mcr.microsoft.com/vscode/devcontainers/java:0-${VARIANT}

# [Option] Install Maven
ARG INSTALL_MAVEN="false"
ARG MAVEN_VERSION=""
# [Option] Install Gradle
ARG INSTALL_GRADLE="false"
ARG GRADLE_VERSION=""
RUN if [ "${INSTALL_MAVEN}" = "true" ]; then su vscode -c "source /usr/local/sdkman/bin/sdkman-init.sh && sdk install maven \"${MAVEN_VERSION}\""; fi \
    && if [ "${INSTALL_GRADLE}" = "true" ]; then su vscode -c "source /usr/local/sdkman/bin/sdkman-init.sh && sdk install gradle \"${GRADLE_VERSION}\""; fi

# [Option] Install Node.js
ARG INSTALL_NODE="true"
ARG NODE_VERSION="lts/*"
RUN if [ "${INSTALL_NODE}" = "true" ]; then su vscode -c "source /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

ARG STRUCTURIZR_CLI_VERSION=latest

RUN apt-get update && apt-get install -y ca-certificates openssl git curl unzip && \
    rm -rf /var/lib/apt/lists/* && \
    case ${STRUCTURIZR_CLI_VERSION} in latest) \
        export STRUCTURIZR_CLI_VERSION=$(curl -s https://api.github.com/repos/structurizr/cli/releases/latest | grep "tag_name" | awk '{print substr($2, 3, length($2)-4)}') ;;\
    esac && \
    echo ${STRUCTURIZR_CLI_VERSION} && \
    wget -O structurizr_cli.zip https://github.com/structurizr/cli/releases/download/v${STRUCTURIZR_CLI_VERSION}/structurizr-cli-${STRUCTURIZR_CLI_VERSION}.zip

RUN unzip structurizr_cli.zip -d /usr/bin/structurizr_cli
#https://github.com/structurizr/cli/releases/download/v1.5.0/structurizr-cli-1.5.0.zip
# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1