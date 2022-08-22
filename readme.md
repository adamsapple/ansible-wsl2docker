# ansible-playbook for using Remote-Container without Docker Desktop

Contents.
<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [features](#features)
- [work procedures](#work-procedures)
  - [1. [windows] Download these and append PATH environment](#1-windows-download-these-and-append-path-environment)
  - [2. [wsl] boot wsl2 and exec ansible playbook](#2-wsl-boot-wsl2-and-exec-ansible-playbook)
  - [3. [windows] use PowerShell](#3-windows-use-powershell)
- [command usage](#command-usage)

<!-- /code_chunk_output -->

## features

- install genie and settings.
- install docker, docker-compose.


playbook: list-tasks:

    play #1 (all): all    TAGS: []
    tasks:
        apt install dependency module.    TAGS: []
        mkdir /etc/apt/trusted.gpg.d      TAGS: []
        download wsl-transdebian.gpg      TAGS: []
        make wsl-transdebian.list TAGS: []
        apt install dotnet5.0 runtine.    TAGS: []
        edit genie.ini.   TAGS: []
        search drive for cloudimg-rootfs(1).      TAGS: []
        search drive for cloudimg-rootfs(2).      TAGS: []
        search drive for cloudimg-rootfs(3).      TAGS: []
        exec e2label      TAGS: []
        exec genie.       TAGS: []
        systemctl set-default     TAGS: []
        systemctl disable getty@tty1      TAGS: []
        systemctl disable multipathd.socket       TAGS: []
        systemctl enable docker   TAGS: []
        systemctl start docker    TAGS: []
        edit docker.service.      TAGS: []
        download docker.gpg       TAGS: []
        docker gpg dearmoring.    TAGS: []
        make docker.list  TAGS: []
        apt install docker.       TAGS: []
        get uname -s      TAGS: []
        get uname -m      TAGS: []
        download docker-compose   TAGS: []
        Create a docker-compose symbolic link     TAGS: []
        get user. TAGS: []
        Add remote user to docker group.  TAGS: []
        edit ~/.bashrc for run genie on login.    TAGS: []



























## work procedures

### 1. [windows] Download these and append PATH environment

- docker https://github.com/StefanScherer/docker-cli-builder/releases
- docker-compose https://github.com/docker/compose/releases

### 2. [wsl] boot wsl2 and exec ansible playbook

    ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass

### 3. [windows] use PowerShell

at Powershell

    Test-NetConnection -ComputerName localhost -Port 2735

If Test-Connection succeessful, create a docker context directed to wsl.

    > docker context create remote --docker 'host=tcp://127.0.0.1:2735'
    > docker context use remote

remote is selected.

    > docker context ls
    NAME       DESCRIPTION                               DOCKER ENDPOINT                  KUBERNETES ENDPOINT   ORCHESTRATOR
    default    Current DOCKER_HOST based configuration   npipe:////./pipe/docker_engine                         swarm
    remote *                                             tcp://127.0.0.1:2735


If successful, client and server versions are displayed.

    > docker version
    Client:
    Version:           20.10.9
    API version:       1.41
    Go version:        go1.13.15
    Git commit:        c2ea9bc90
    Built:             10/13/2021 11:55:06
    OS/Arch:           windows/amd64
    Context:           remote
    Experimental:      true

    Server: Docker Engine - Community
    Engine:
    Version:          20.10.17
    API version:      1.41 (minimum version 1.12)
    Go version:       go1.17.11
    Git commit:       a89b842
    Built:            Mon Jun  6 23:01:03 2022
    OS/Arch:          linux/amd64
    Experimental:     false
    containerd:
    Version:          1.6.7
    GitCommit:        0197261a30bf81f1ee8e6a4dd2dea0ef95d67ccb
    runc:
    Version:          1.1.3
    GitCommit:        v1.1.3-0-g6724737
    docker-init:
    Version:          0.19.0
    GitCommit:        de40ad0

## command usage

simple.

    ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass

select task.

    ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass --step --start-at='foo' -vvv
