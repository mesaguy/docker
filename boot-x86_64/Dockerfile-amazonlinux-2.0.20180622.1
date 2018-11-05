# Source
FROM amazonlinux:2.0.20180622.1

# Clean (purge) the repo cache
RUN yum -d1 -y clean all && \
# Update system-release to test inspec and other testers
yum -d1 -y update system-release && \
# Install systemctl
yum -d1 -y install systemd systemd-libs dbus && \
# Strip down systemd
find /lib/systemd/system/sysinit.target.wants -type l ! -name systemd-tmpfiles-setup.service -delete && \
rm -f /lib/systemd/system/multi-user.target.wants/* && \
rm -f /etc/systemd/system/*.wants/* && \
rm -f /lib/systemd/system/local-fs.target.wants/* && \
rm -f /lib/systemd/system/sockets.target.wants/*udev* && \
rm -f /lib/systemd/system/sockets.target.wants/*initctl* && \
rm -f /lib/systemd/system/basic.target.wants/* && \
rm -f /lib/systemd/system/anaconda.target.wants/* && \
# Clean (purge) the repo cache
yum -d1 -y clean all && rm -rf /var/cache/yum/* && \
# Purge logs
rm -rf /var/log/* /var/run/log/journal

# Without this, init won't start the enabled services. Starting the services
# fails with one of:
#     Failed to get D-Bus connection: Operation not permitted
#     System has not been booted with systemd as init system (PID 1). Can't operate.
#     Failed to connect to bus: No such file or directory
VOLUME [ "/sys/fs/cgroup", "/run" ]

# Start via systemd
CMD ["/usr/lib/systemd/systemd"]

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Amazon Linux v2 (2.0.20180622.1) boot" \
      org.label-schema.description="Image boots Amazon Linux v2 (2.0.20180622.1) via systemd" \
      com.mesaguy.operatingsystem.eol="false"
