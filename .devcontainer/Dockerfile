FROM ghcr.io/ansible/community-ansible-dev-tools:v26.4.6

# Install System Packages & Utilities
ARG FEDORA_VERSION=42
ARG POWERSHELL_VERSION=7.6.2

RUN curl -SL https://download.docker.com/linux/fedora/docker-ce.repo -o /etc/yum.repos.d/docker-ce.repo && \
    sed -i 's/\$releasever/'"${FEDORA_VERSION}"'/g' /etc/yum.repos.d/docker-ce.repo && \
    dnf install -y --nogpgcheck \
        docker-ce-cli \
        docker-compose-plugin \
        iputils \
        "https://github.com/PowerShell/PowerShell/releases/download/v${POWERSHELL_VERSION}/powershell-${POWERSHELL_VERSION}-1.rh.x86_64.rpm" && \
    dnf update -y && \
    dnf clean all

# Copy dependency files to cache Python/Ansible packages
COPY requirements.txt requirements.yml /tmp/dependencies/

# Install Python requirements & Ansible Collections
RUN pip install -r /tmp/dependencies/requirements.txt && \
    ansible-galaxy install -r /tmp/dependencies/requirements.yml

# Dynamically find and install requirements from the installed collections
RUN if [ -d ~/.ansible/collections/ansible_collections ]; then \
        grep -oE '\s*-\s*name:\s*[a-zA-Z0-9_.-]+' /tmp/dependencies/requirements.yml | awk '{print $NF}' | while read -r col; do \
            col_path=$(echo "$col" | tr '.' '/') && \
            req_file="$HOME/.ansible/collections/ansible_collections/$col_path/requirements.txt" && \
            if [ -f "$req_file" ]; then \
                echo "Installing Python dependencies for collection '$col' from $req_file..." && \
                pip install -r "$req_file"; \
            fi; \
        done; \
    fi && \
    rm -rf /tmp/dependencies
