FROM mesaguy/debian-9-boot-x86_64:latest

# Update repo definitions
RUN apt update && \
# Install sudo and openssh for kitchen
apt install -y openssh-server sudo && \
# Clean (purge) the repo cache
apt-get clean && \
rm -rf /var/lib/apt/lists/* && \
# Purge logs
rm -rf /var/log/*

# Adjust sshd defaults per kitchen's needs
RUN test -f /usr/lib/openssh/sftp-server && \
printf "Subsystem sftp /usr/lib/openssh/sftp-server\\nUseDNS no\\nUsePAM no\\nPasswordAuthentication yes\\nUsePrivilegeSeparation no\\n" > /etc/ssh/sshd_config && \
# Start SSH on boot
update-rc.d ssh defaults && \
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
      org.label-schema.name="Debian Linux 9 (Stretch) kitchen-base" \
      org.label-schema.description="Image boots Debian Linux 9 (Stretch) via systemd configured for kitchen testing" \
      com.mesaguy.operatingsystem.eol="false"
