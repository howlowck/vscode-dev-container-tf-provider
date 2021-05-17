# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.163.1/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version: bionic, focal
ARG VARIANT="ubuntu-20.04"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends build-essential vim

ARG GO_VERSION=1.16.4
ARG TERRAFORM_VERSION=0.15.3
ARG HOME="/home/vscode"

#####################
# Install GO
#####################
RUN mkdir gotemp \
    && cd gotemp \
    && wget https://dl.google.com/go/go${GO_VERSION}.linux-amd64.tar.gz \
    && tar -xvf go${GO_VERSION}.linux-amd64.tar.gz \
    && mv go /usr/local
ENV GOROOT=/usr/local/go
ENV GOPATH=$HOME/go
ENV PATH=$GOPATH/bin:$GOROOT/bin:$PATH

#####################
# Install Terraform
#####################
RUN wget --progress=dot:mega https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip
RUN \
	unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
	mv terraform /usr/local/bin/ && \
	chmod +x /usr/local/bin/terraform && \
	terraform --version

#####################
# Install Az CLI
#####################
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

#####################
# Setup Environment
#####################
RUN \
    echo "alias setenv='export \$(grep -v '^#' .env | xargs)'" >> ~/.bashrc && \
    echo "alias setenv='export \$(grep -v '^#' .env | xargs)'" >> ~/.zshrc
