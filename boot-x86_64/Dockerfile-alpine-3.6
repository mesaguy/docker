# Source
FROM alpine:3.6

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
      org.label-schema.name="Alpine Linux 3.6 boot" \
      org.label-schema.description="Image boots Alpine Linux 3.6 via OpenRC" \
      com.mesaguy.operatingsystem.eol="false"
