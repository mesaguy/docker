FROM mesaguy/archlinux-boot-x86_64:latest

# Update repo definitions
RUN pacman -Sy --noconfirm && \
# Install sudo and openssh for kitchen
pacman --noconfirm -S sudo openssh && \
# Clean (purge) the repo cache
pacman --noconfirm -Scc && rm -rf /var/lib/pacman/sync/* && \
# Purge logs
rm -rf /var/log/* /var/run/log/journal

# Adjust sshd defaults per kitchen's needs
RUN test -f /usr/lib/ssh/sftp-server && \
printf "Subsystem sftp /usr/lib/ssh/sftp-server\\nUseDNS no\\nUsePAM no\\nPasswordAuthentication yes\\nUsePrivilegeSeparation no\\n" > /etc/ssh/sshd_config && \
# Start SSH on boot
systemctl enable sshd.service && \
# Add 'kitchen' user
if ! getent passwd kitchen; then useradd -d /home/kitchen -m -s /bin/bash -p '*' kitchen; fi && \
# Allow unlimited sudo privileges to 'kitchen' user
echo "kitchen ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers && echo "Defaults !requiretty" >> /etc/sudoers && \
# Make 'kitchen' user's ~/.ssh directory
mkdir -m 0700 /home/kitchen/.ssh && \
# Make 'kitchen' user's authorized_keys file (empty)
touch /home/kitchen/.ssh/authorized_keys && \
# Secure 'kitchen' user's authorized_keys file
chmod 0600 /home/kitchen/.ssh/authorized_keys && \
# Fix 'kitchen' user's SSH directory permissions
chown -R kitchen:kitchen /home/kitchen/.ssh

# Expose SSH
EXPOSE 22

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="ArchLinux latest rolling-release kitchen-base" \
      org.label-schema.description="Image boots ArchLinux's latest rolling-release via systemd configured for kitchen testing" \
      com.mesaguy.operatingsystem.eol="false"
