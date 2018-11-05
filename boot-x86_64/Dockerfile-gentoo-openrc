# Source
FROM gentoo/stage3-amd64:latest

# Sync portage
RUN mkdir -p /usr/portage/distfiles /usr/portage/metadata /usr/portage/packages && \
chown -R portage:portage /usr/portage && \
emerge-webrsync && \
# Add required base packages
emerge app-portage/gentoolkit && \
# Tell openrc loopback and net are already there, since docker handles the networking
echo 'rc_provide="loopback net"' >> /etc/rc.conf && \
# Can't get ttys unless you run the container in privileged mode
sed -i '/tty/d' /etc/inittab && \
# Can't set hostname since docker sets it
sed -i "s/hostname \$opts/# hostname \$opts/g" /etc/init.d/hostname && \
# Can't mount tmpfs since not privileged
sed -i 's/mount -t tmpfs/# mount -t tmpfs/g' /lib/rc/sh/init.sh && \
# Can't do cgroups
sed -i 's/cgroup_add_service /# cgroup_add_service /g' /lib/rc/sh/openrc-run.sh && \
# Disable services
rc-update delete loopback boot && \
rc-update delete netmount default && \
# Remove troublesome and worthless start scripts
rm -rf /etc/init.d/bootmisc /etc/init.d/udev-settle /etc/init.d/udev /etc/init.d/udev-trigger /run/openrc && \
mkdir -p /run/openrc && \
echo "default" > /run/openrc/softlevel && \
# Cleanup portage, downloaded source files and compile directories
rm -rf /usr/portage /var/tmp/* && \
# Purge logs
rm -rf /var/log/*

# Start via init
CMD ["/sbin/init"]

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Gentoo Linux latest rolling-release boot" \
      org.label-schema.description="Image boots Gentoo Linux's latest rolling-release via SysV init" \
      com.mesaguy.operatingsystem.eol="false"
