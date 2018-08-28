FROM mesaguy/fedora-26-kitchen-base-x86_64:latest

# Clean (purge) the repo cache
RUN dnf -y clean all && \
# Install python 2.7
dnf -y install python && \
# Clean (purge) the repo cache
dnf -y clean all && rm -rf /var/cache/dnf/* /var/cache/yum/* && \
# Purge logs
rm -rf /var/log/* /var/run/log/journal

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Fedora Linux 26 kitchen-ansible" \
      org.label-schema.description="Image boots Fedora Linux 26 via systemd configured for kitchen ansible testing" \
      com.mesaguy.operatingsystem.eol="true"
