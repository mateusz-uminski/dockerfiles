# debian12-systemd

Debian12 container image with systemd support for testing ansible roles.

# Usage

## Build
```sh
cd $(git rev-parse --show-toplevel)
docker build -t debian12-systemd debian12-systemd/
```

## Run
```sh
docker run -d --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host debian12-systemd /sbin/init
```
Note: [Failed to connect to bus](https://www.jeffgeerling.com/blog/2022/docker-and-systemd-getting-rid-dreaded-failed-connect-bus-error)
