FROM mesaguy/alpine-edge-kitchen-base-x86_64:latest

# Install python and shadow (user and group management)
RUN apk add --no-cache python shadow && \
# Purge logs
rm -rf /var/log/*

# Image metadata
LABEL org.label-schema.vendor="Mesaguy" \
      org.label-schema.name="Alpine Linux edge kitchen-ansible" \
      org.label-schema.description="Image boots Alpine Linux edge via OpenRC configured for kitchen ansible testing" \
      com.mesaguy.operatingsystem.eol="false"
