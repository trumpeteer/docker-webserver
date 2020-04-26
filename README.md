# docker-webserver
Docker-based web server running apps behind a reverse proxy.

## Prerequisites

1. Install Docker and docker-compose
2. Create docker network
    Some apps can get complicated when mapping ports.
    For this reason I like to use macvlan networks (replace variables with your acutal values):
        docker network create -d macvlan -o parent=$HOST_NETWORK_INTERFACE_NAME --subnet=$HOST_NETWORK_CIDR --gateway=$NETWORK_GATEWAY --ip-range=$DOCKER_NETWORK_CIDR $DOCKER_NETWORK_RANGE
        my example: docker network create -d macvlan -o parent=enp31s0 --subnet=10.1.10.1/16 --gateway=10.1.0.1 --ip-range=10.1.11.0/24 traefik
3. Domain with root DNS (I use Cloudflare DNS hosting) pointed at your public IP.
