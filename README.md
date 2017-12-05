# GalliumOS 2.1 Ansible Test Image

[![Docker Automated build](https://img.shields.io/docker/automated/polymimetic/docker-gallium-ansible.svg?maxAge=2592000)](https://hub.docker.com/r/polymimetic/docker-gallium-ansible/)
[![Build Status](https://travis-ci.org/polymimetic/docker-gallium-ansible.svg?branch=master)](https://travis-ci.org/polymimetic/docker-gallium-ansible)

GalliumOS 2.1 Docker container for Ansible playbook and role testing.

## How to Build

This image is built on Docker Hub automatically any time the upstream OS container is rebuilt, and any time a commit is made or merged to the `master` branch. But if you need to build the image on your own locally, do the following:

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. `cd` into this directory.
  3. Run `docker build -t gallium-ansible .`

## How to Use

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. Pull this image from Docker Hub: `docker pull polymimetic/docker-gallium-ansible:latest` (or use the tag you built earlier, e.g. `gallium-ansible`).
  3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro polymimetic/docker-gallium-ansible:latest /lib/systemd/systemd` (to test Ansible roles, add in a volume mounted from the current working directory with ``--volume=`pwd`:/etc/ansible/roles/role_under_test:ro``).
  4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

## Notes

This container allows for testing roles and playbooks using Ansible running locally inside the container.

> **Important Note**: This image is for testing in an isolated environment—not for production—and the settings and configuration used may not be suitable for a secure and performant production environment. Use on production servers/in the wild at your own risk!

## Author

Created in 2016 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).

Slightly modified by [Polymimetic](https://github.com/polymimetic) for testing [GalliumOS](https://galliumos.org/) based Chromebooks.
