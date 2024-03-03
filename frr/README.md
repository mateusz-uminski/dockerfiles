# frr

Frr container image used for creating network labs.

# Usage

## Build
```sh
cd $(git rev-parse --show-toplevel)
docker build -t frr frr/
```

## Run
```sh
docker run -d --cap-add=SYS_ADMIN --cap-add=NET_ADMIN --sysctl net.ipv4.ip_forward=1 frr
```
