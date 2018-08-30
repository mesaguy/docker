# Source
FROM amazonlinux:2016.09

# Clean (purge) the repo cache
RUN yum -d1 -y clean all && \
# Install init scripts
yum install -y initscripts && \
# Disable all services
rm /etc/rc.d/rc*.d/* && \
# Disable ttys
mv /etc/init/serial.conf /etc/init/serial.conf.disabled && \
mv /etc/init/tty.conf /etc/init/tty.conf.disabled && \
mv /etc/init/start-ttys.conf /etc/init/start-ttys.conf.disabled && \
# Clean (purge) the repo cache
yum -d1 -y clean all && rm -rf /var/cache/yum/* && \
# Purge logs
rm -rf /var/log/*

# Start via init
CMD ["/sbin/init"]

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Amazon Linux v1 (2016.09) boot" \
      org.label-schema.description="Image boots Amazon Linux v1 (2016.09) via SysV init" \
      com.mesaguy.operatingsystem.eol="false"
