FROM mesaguy/archlinux-kitchen-base-x86_64:latest

# Update repo definitions
RUN pacman -Sy --noconfirm && \
# Install puppet for kitchen
pacman --noconfirm -S python && \
# Clean (purge) the repo cache
pacman --noconfirm -Scc && rm -rf /var/lib/pacman/sync/* && \
# Purge logs
rm -rf /var/log/* /var/run/log/journal

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="ArchLinux latest rolling-release kitchen-ansible" \
      org.label-schema.description="Image boots ArchLinux's latest rolling-release via systemd configured for kitchen ansible testing" \
      com.mesaguy.operatingsystem.eol="false"
