# docker-devuan
[![License][license-img]][license-href]
[![docker][docker-img]][docker-href]

## Overview

Devuan is  a free software  operating system  for your computer.  Free software
means you are free to use, copy and distribute, study, change the software, and
share your modifications with the community.

[devuan.org](https://www.devuan.org/)

## Description

Use this script to build your own base system or use the travis build base images from Docker Hub.

I (queercodinggirl) forked this repo from [https://github.com/vente-privee/docker-devuan] and fixed the build script because it wasn't able to build the ascii image and had no support for beowulf. Also i don't wanted to use their CI system. This repo now uses travis-ci and builds/pushes all devuan releases at a regular interval.

## Tags

Supported tags.

- 1, jessie, oldoldstable
- 2, ascii, oldstable
- 3, beowulf, stable, latest
- 4, chimaera, testing

## Requirements

On Debian you need sudo permissions and the following packages:

```bash
# if you build on wheezy please use backports version of debootstrap
$ sudo apt-get -qq -y install debootstrap
```

On Devuan you need sudo permissions and the following packages:

```bash
$ sudo apt-get -qq -y install debootstrap
```

On Ubuntu you need sudo permissions and the following packages:

```bash
$ sudo apt-get -qq -y install debian-keyring debian-archive-keyring debootstrap
```

You also need to be in the docker group to use Docker.

```bash
$ sudo usermod -a -G docker ${USER}
```

Finally you need to login on Docker Hub.

```bash
$ docker login
```

## Usage

You first need  to choose which dist  between jessie (1.0) and  beowulf (3.0) you
want (ascii  will be the  'latest' tag)  and you need  to choose you  user (or
organization) name on Docker Hub.

Show help.

```bash
$ ./build.sh -h
```

Build your own Debian image (eg. jessie).

```bash
$ ./build.sh -d jessie -u queercodinggirl
```

Build your own Devuan image (eg. ascii) and push it on the Docker Hub.

```bash
$ ./build.sh -d ascii -u queercodinggirl -p
```

## Limitations

Only work on Debian, Devuan and Ubuntu.

## Development

Please read carefully [CONTRIBUTING.md][contribute-href]  before making a merge
request.


[license-img]: https://img.shields.io/badge/license-Apache-blue.svg
[license-href]: /LICENSE
[docker-img]: https://img.shields.io/docker/pulls/queercodinggirl/devuan.svg
[docker-href]: https://registry.hub.docker.com/u/queercodinggirl/devuan
[contribute-href]: /CONTRIBUTING.md
