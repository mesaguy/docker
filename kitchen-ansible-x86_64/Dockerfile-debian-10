FROM mesaguy/debian-10-kitchen-base-x86_64:latest

# Update repo definitions
RUN apt update && \
# Install lsb-release and python for ansible
apt install -y lsb-release python && \
# Clean (purge) the repo cache
apt-get clean && \
rm -rf /var/lib/apt/lists/* && \
# Purge logs
rm -rf /var/log/*

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Debian Linux 10 (Buster) kitchen-ansible" \
      org.label-schema.description="Image boots Debian Linux 10 (Buster) via systemd configured for kitchen ansible testing" \
      com.mesaguy.operatingsystem.eol="false"
