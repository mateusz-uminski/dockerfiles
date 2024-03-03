# alma9-systemd

Almalinux9 container image with systemd support for testing ansible roles.

# Usage

## Build
```sh
cd $(git rev-parse --show-toplevel)
docker build -t alma9-systemd alma9-systemd/
```

## Run
```sh
docker run -d --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host alma9-systemd /sbin/init
```
Note: [Failed to connect to bus](https://www.jeffgeerling.com/blog/2022/docker-and-systemd-getting-rid-dreaded-failed-connect-bus-error)
