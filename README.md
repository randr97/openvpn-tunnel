# Openvpn proxy - M1 chip (tested) [In Progress]

> The below projects, I had a difficulty in running it on M1 chip, so this is my workaround

*Credits*
- https://github.com/kizzx2/docker-openvpn-client-socks
- https://github.com/mook/docker-openvpn-client-socks

## steps to follow
1. Download and install docker for M1
2. Place your openvpn file in the folder `$HOME/openvpn/data/<your-file-name>.conf`
3. Clone this repo and run `docker build -t openvpn-connect .`
4. To run the vpn-proxy at port 1080
```
docker run \
    -it --rm \
    --device=/dev/net/tun \
    --cap-add=NET_ADMIN \
    --name=openvpn-client \
    --volume $HOME/openvpn/data/:/etc/openvpn/:ro \
    -p 1080:1080 \
    openvpn-connect
```
