# Ansible

Ansible inside Docker for consistent running of ansible inside your local machine or CI/CD system.

[![Docker Pulls](https://img.shields.io/docker/pulls/willhallonline/ansible.svg)][hub] [![](https://images.microbadger.com/badges/image/willhallonline/ansible.svg)](https://microbadger.com/images/willhallonline/ansible "Get your own image badge on microbadger.com") [![Docker Automated build](https://img.shields.io/docker/automated/willhallonline/ansible.svg)][hub] [![Docker Build Status](https://img.shields.io/docker/build/willhallonline/ansible.svg)][hub]

## Supported tags and respective ```Dockerfile``` links

### Ansible 2.7 (with Mitogen)

**This is my preferred install variant mainly due to the performance improvements that Mitogen awards you. You can read more about it inside the [Mitogen for Ansible documentation](https://mitogen.readthedocs.io/en/stable/ansible.html).**

* ```latest```, ```2.7```, ```alpine```, ```2.7-alpine```, ```alpine-3```, ```2.7-alpine-3```,  ```alpine-3.9```, ```2.7-alpine-3.9``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible27/alpine39/Dockerfile) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/willhallonline/ansible/alpine.svg)
* ```alpine-3.8```, ```2.7-alpine-3.8``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible27/alpine38/Dockerfile) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/willhallonline/ansible/alpine.svg)
* ```ubuntu```, ```2.7-ubuntu```, ```ubuntu-18.04```, ```2.7-ubuntu-18.04``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible27/ubuntu1804/Dockerfile) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/willhallonline/ansible/ubuntu.svg)
* ```ubuntu-16.04```, ```2.7-ubuntu-16.04``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible27/ubuntu1604/Dockerfile)
* ```centos```, ```centos-7```, ```2.7-centos```, ```2.7-centos-7``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible27/centos7/Dockerfile) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/willhallonline/ansible/centos.svg)

### Ansible 2.5 (with Mitogen)

* ```2.5```, ```2.5-alpine```, ```2.5-alpine-3```, ```2.5-alpine-3.9``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible25/alpine39/Dockerfile) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/willhallonline/ansible/2.5.svg)
* ```2.5-alpine-3.8``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible25/alpine38/Dockerfile)
* ```2.5-ubuntu```, ```2.5-ubuntu-18.04``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible25/ubuntu1804/Dockerfile) ![MicroBadger Layers](https://img.shields.io/microbadger/layers/willhallonline/ansible/2.5-ubuntu.svg)
* ```2.5-ubuntu-16.04``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible25/ubuntu1604/Dockerfile)
* ```2.5-centos```, ```2.5-centos-7``` [Dockerfile](https://github.com/willhallonline/docker-ansible/blob/master/ansible25/centos7/Dockerfile)

To leverage *Mitogen* to accelerate your playbook runs, add this to your ```ansible.cfg```:

```
strategy_plugins = /usr/lib/python2.7/site-packages/ansible_mitogen/plugins/strategy
strategy = mitogen_linear
```

## Running

**You will likely need to mount required directories into your container to make it run (or build on top of what is here).

### Simple

```
$   docker run --rm -it willhallonline/ansible /bin/sh
```

### Mount local directory and ssh key

```
$   docker run --rm -it -v $(pwd):/ansible -v ~/.ssh/id_rsa:/root/id_rsa willhallonline/ansible:2.7 /bin/sh
```

### Injecting commands

```
$   docker run --rm -it -v $(pwd):/ansible -v ~/.ssh/id_rsa:/root/id_rsa willhallonline/ansible:2.7 ansible-playbook playbook.yml
```

### Bash Alias

You can put these inside your dotfiles (~/.bashrc or ~/.zshrc to make handy aliases).

```
alias docker-ansible-cli='docker run --rm -it -v $(pwd):/ansible -v ~/.ssh/id_rsa:/root/.ssh/id_rsa --workdir=/ansible willhallonline/ansible:2.7-alpine /bin/sh'
alias docker-ansible-cmd='docker run --rm -it -v $(pwd):/ansible -v ~/.ssh/id_rsa:/root/.ssh/id_rsa --workdir=/ansible willhallonline/ansible:2.7-alpine '
```

use with:

```
$  docker-ansible-cli ansible-playbook -u playbook.yml
```

## Maintainer

* Written and maintained by Will Hall (https://www.willhallonline.co.uk)

[hub]: https://hub.docker.com/r/willhallonline/ansible
[microbadger]: https://microbadger.com/images/willhallonline/ansible
