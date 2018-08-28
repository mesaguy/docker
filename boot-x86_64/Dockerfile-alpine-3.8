# Source
FROM alpine:3.8

# Install openrc
RUN apk --no-cache add openrc && \
# Disable ttys
sed -i 's/^tty/#tty/g' /etc/inittab && \
# Purge logs
rm -rf /var/log/*

# Needed by OpenRC
VOLUME [ "/run" ]

# Start via init
CMD ["/sbin/init"]

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Alpine Linux 3.8 boot" \
      org.label-schema.description="Image boots Alpine Linux 3.8 via OpenRC" \
      com.mesaguy.operatingsystem.eol="false"
