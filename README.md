# Ansible Sandbox

## Overview

An Ansible (playbook test) rootless Podman container with `systemd`, `ansible` and `podman`, based on Rocky Linux 9.

## Rationale

Could not find a RHEL-like Podman rootless-compatible image not based on RHEL (subscription required)
running `systemd` and able to run `podman` inside (for Ansible playbooks deploying Podman containers).

## Usage

This repository is intended to be cloned inside the root of a repository containing your Ansible playbooks.

### Setup

To set up the Ansible sandbox with all features:

```
./ansible-sandbox up
```

### Ansible testing

Once the container is up and running, execute `ansible` commands as the `ansible` user.

Your Ansible playbooks are mounted in and should be available at `/home/ansible/source/`.

### Podman in Podman testing

The `container` user is set up and intended for testing Podman container deployments with Ansible.

Containers are created inside the Ansible sandbox container, leaving your host environment untouched.

### Setup to specific feature level

The Ansible sandbox supports setting up with different feature levels:

```
./ansible-sandbox up --feature-level ansible
```

- `ansible`: Rocky Linux 9 + Ansible installed
- `podman`: Rocky Linux 9 + Ansible + Podman installed

### Tear down

To tear down the Ansible sandbox:

```
./ansible-sandbox down
```

### Help

The `--help` long option flag is available for all commands and sub-commands.

## If you encounter an issue

Please open an issue, providing as much detail as possible about the steps you took before the issue occurred,
as well as details about your environment (OS, Podman, Ansible versions).

## Contribution

If you see something that could be improved (there is plenty of room for improvement) or would like to contribute a bug-fix or a feature to this project,
feel free to open a pull request.

## Credits / Inspiration

- https://github.com/containers/image_build/blob/main/podman/Containerfile
- https://github.com/eniocarboni/docker-rockylinux-systemd/blob/main/Dockerfile
- https://github.com/geerlingguy/docker-ubi8-ansible/blob/master/Dockerfile
- https://www.redhat.com/sysadmin/podman-inside-container
- https://github.com/shakibamoshiri/bash-CLI-template/tree/master
