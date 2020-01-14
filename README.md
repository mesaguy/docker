# Docker images for testing
[![Build Status](https://api.travis-ci.org/mesaguy/docker.svg?branch=master)](https://travis-ci.org/mesaguy/docker)

These images exist exclusively for testing software. These images should not be used in any production capacity.

Two forms of images are available:
 1. [Bootable images](https://github.com/mesaguy/docker/tree/master/boot-x86_64) - These images boot via systemd, upstart, openrc, etc, but start no services.
 3. [Kitchen ansible images](https://github.com/mesaguy/docker/tree/master/kitchen-ansible-x86_64) - These images build upon the 'Bootable images' above, but enable SSH, configure a 'kitchen' user for use via SSH. These images also ensure python and basic ansible prerequisite software is installed

# Author Information
Mesaguy
 - https://github.com/mesaguy/docker
 - https://mesaguy.com
