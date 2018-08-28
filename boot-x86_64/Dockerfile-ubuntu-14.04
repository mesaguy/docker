# Source
FROM ubuntu-upstart:14.04

# Update repo definitions
RUN apt update && \
# Upgrade all packages
apt dist-upgrade -y && \
# Remove udev and tty startups
rm -f /etc/init.d/console-setup /etc/init.d/udev && \
# Clean (purge) the repo cache
apt-get clean && \
rm -rf /var/lib/apt/lists/* && \
# Purge logs
rm -rf /var/log/*

# Start via init
CMD ["/sbin/init"]

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Ubuntu Linux 14.04 (Trusty Tahr) boot" \
      org.label-schema.description="Image boots Ubuntu Linux 14.04 (Trusty Tahr) via Upstart" \
      com.mesaguy.operatingsystem.eol="false"
