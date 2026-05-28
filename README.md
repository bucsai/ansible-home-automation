# Ansible Development Template

This is a personal template repository for cross-platform Ansible development. It utilizes a dev container to provide a consistent and fully-featured environment for writing, testing, and managing Ansible playbooks and roles.

## Features

*   **Pre-configured Dev Container:** Get started quickly without installing dependencies on your local machine.
*   **Ansible Ready:** Includes all necessary tools for Ansible development.

### Included Tools

The dev container environment is pre-installed with:
*   **Ansible Dev Tools:** Based on `community-ansible-dev-tools` (provides `ansible`, `ansible-lint`, etc.).
*   **Docker CLI & Compose Plugin:** For container management (mapped to the host's Docker socket `/var/run/docker.sock`).
*   **PowerShell 7 (pwsh):** Cross-platform PowerShell for writing and testing Windows-targeted scripts.
*   **Python Packages:** `requests` and `pywinrm` (supporting WinRM connections).
*   **Network Utilities:** `iputils` for connectivity testing.

### VS Code Extensions

The following VS Code extensions are pre-configured and installed inside the container:
*   **Ansible** (`redhat.ansible`)
*   **Container Tools** (`ms-azuretools.vscode-containers`)
*   **Ruff** (`charliermarsh.ruff`)
*   **PowerShell** (`ms-vscode.powershell`)

## AI Agent Guidelines

This repository contains an [AGENTS.md](AGENTS.md) file that provides context and development guidelines for AI coding assistants (such as Antigravity/Agy).

> [!NOTE]
> The configurations and instructions in `AGENTS.md` are specific to this particular development environment. Anyone utilizing this repository should adjust `AGENTS.md` to fit their own workspace configuration.

## Getting Started

1.  Clone this repository.
2.  Open the project in a supporting IDE (like VS Code) with the Dev Containers extension installed.
3.  When prompted, reopen the folder in the container.
