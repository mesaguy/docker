# Docker images for kitchen ansible based testing
[![Build Status](https://api.travis-ci.org/mesaguy/docker.svg?branch=master)](https://travis-ci.org/mesaguy/docker)

Images are bootable for use by [kitchen](https://github.com/test-kitchen/test-kitchen) via SSH.

# Usage

## Install Ruby gems
The following Ruby gems will need to be installed:

    gem install kitchen-docker
    gem install test-kitchen

## Create a dummy Dockerfile
Create a dummy Dockerfile in your project. This is Dockerfile will add the unique keys that your kitchen instance generates to this project's docker images

    cat > tests/Dockerfile << EOF
    ARG DOCKER_IMAGE_NAME
    FROM $DOCKER_IMAGE_NAME
    # Add your specific Ansible SSH public key. This only works when run via
    # kitchen, when run with the following options in your .kitchen.yml file:
    #
    #    driver_config:
    #      build_options:
    #        build-arg: SSH_KEY=<%= File.read('.kitchen/docker_id_rsa.pub') %>
    #
    ARG SSH_KEY
    RUN echo "$SSH_KEY" >> /home/kitchen/.ssh/authorized_keys
    EOF

## Setup a kitchen configuration file
See [Kitchen Ansible Docker](https://github.com/test-kitchen/kitchen-docker) documentation and the [Kitchen example file](https://github.com/mesaguy/docker/blob/master/kitchen-ansible-x86_64/kitchen.yml)

The kitchen example file is almost complete, it only requires a kitchen provisioner (Ansible, Chef, Puppet, etc) be defined before use.

Create an SSH key for testing with kitchen:

    ssh-keygen -f .kitchen/docker_id_rsa -t rsa -N ''

## Run kitchen
See the available test platforms:

    kitchen list

Run all tests via:

    kitchen test

Or run specific platform tests via:

    kitchen test [[platforms from 'kitchen list']]


# Author Information
Mesaguy
- https://github.com/mesaguy/docker
- https://mesaguy.com
