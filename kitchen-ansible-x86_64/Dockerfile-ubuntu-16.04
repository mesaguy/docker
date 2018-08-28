FROM mesaguy/ubuntu-16.04-kitchen-base-x86_64:latest

# Update repo definitions
RUN apt update && \
# Install python for ansible
apt install -y python && \
# Clean (purge) the repo cache
apt-get clean && \
rm -rf /var/lib/apt/lists/* && \
# Purge logs
rm -rf /var/log/*

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Ubuntu Linux 16.04 (Xenial Xerus) kitchen-ansible" \
      org.label-schema.description="Image boots Ubuntu Linux 16.04 (Xenial Xerus) via systemd configured for kitchen ansible testing" \
      com.mesaguy.operatingsystem.eol="false"
