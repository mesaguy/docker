FROM mesaguy/opensuse-leap-kitchen-base-x86_64:latest

# Install python for ansible
RUN zypper --non-interactive install --no-confirm python python-xml && \
# Clean (purge) the repo cache
zypper --non-interactive clean --all && \
# Purge logs
rm -rf /var/log/* /var/run/log/journal

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="OpenSUSE Linux leap kitchen-ansible" \
      org.label-schema.description="Image boots OpenSUSE Linux leap via systemd configured for kitchen ansible testing" \
      com.mesaguy.operatingsystem.eol="false"
