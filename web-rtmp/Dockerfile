# Docker certbot based on:
# https://www.humankode.com/ssl/how-to-set-up-free-ssl-certificates-from-lets-encrypt-using-docker-and-nginx

FROM tiangolo/nginx-rtmp
#RUN apt-get install build-essential libpcre3 libpcre3-dev libssl-dev
#RUN wget https://github.com/sergey-dryabzhinsky/nginx-rtmp-module/archive/dev.zip
#COPY html /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf


# From https://linuxconfig.org/how-to-install-nodejs-on-debian-9-stretch-linux
# Install nodejs
RUN mkdir -p /tmp/nodejs && \
    cd /tmp/nodejs && \
    curl -sL https://deb.nodesource.com/setup_10.x > setup_10.x && \
    chmod +x setup_10.x && \
    ./setup_10.x

RUN apt install -y nodejs build-essential libssl-dev

# Need to start the websocket server
# Overrides CMD from original dockerfile
# TODO: split out websocket server into its own container
CMD cd /usr/share/nginx/html/webrtc_simple && \
    npm start & \
    nginx -g "daemon off;"
