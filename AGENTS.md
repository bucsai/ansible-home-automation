# Agent Context and Instructions

This file contains context, guidelines, and rules for AI agents (including `agy` and others) operating in this workspace.

## System Context & Environment

1. **Host OS:** You are running on a Windows 11 Pro workstation.
2. **Ansible Environment:** Ansible-related questions and tasks refer to a development environment running on the same host inside Docker on WSL2. Ansible CLI commands (e.g., `ansible-playbook`) can be run inside the active container by executing `docker compose -f .devcontainer/docker-compose.yaml -p <folder_name>_devcontainer exec ansible <command>` from the workspace root directory (replacing `<folder_name>` with the current project folder name, e.g., `ansible-dev-template`). If this fails, find the active container name using `docker ps` and run `docker exec`.

## Ansible Guidelines

1. **Fully-Qualified Collection Names (FQCN):** For Ansible, always use fully-qualified collection names (e.g., `ansible.builtin.copy` instead of `copy`, `community.general.git` instead of `git`).
2. **Native Ansible Design Patterns:** Prefer native Ansible features (e.g., `environment:`, variable inheritance, `pre_tasks`/`post_tasks`) rather than relying on OS-level workarounds (e.g., writing to shell startup files like `.bashrc` or `.zshrc` to pass values between tasks).

## Testing Guidelines

1. **Automatic Testing:** Do not run tests automatically or during thinking phases. Only run tests when explicitly asked to do so by the user.
