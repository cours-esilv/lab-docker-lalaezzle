# Use Nginx base image from Docker Hub
FROM nginx:alpine

# Copy static content
COPY index.html /usr/share/nginx/html/
COPY style.css /usr/share/nginx/html/

# Embed the entrypoint script directly
RUN echo $'#!/bin/sh\n\
set -euo pipefail\n\
: ${WS_BACK_URL:=http://localhost:8080}\n\
echo "Will start Nginx with the following configuration:"\n\
echo "  - WS_BACK_URL : $WS_BACK_URL"\n\
sed -i "s@TR_WS_BACK_URL@$WS_BACK_URL@" /usr/share/nginx/html/index.html\n\
exec nginx -g "daemon off;"' > /entrypoint.sh && chmod +x /entrypoint.sh

# Environment variable with a default value
ENV WS_BACK_URL=http://localhost:8080

# Use the custom entrypoint script
ENTRYPOINT ["/entrypoint.sh"]