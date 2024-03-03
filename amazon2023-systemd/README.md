# amazon2023-systemd

Amazon2023 container image with systemd support for testing ansible roles.

# Usage

## Build
```sh
cd $(git rev-parse --show-toplevel)
docker build -t amazon2023-systemd amazon2023-systemd/
```

## Run
```sh
docker run -d --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host amazon2023-systemd /sbin/init
```
Note: [Failed to connect to bus](https://www.jeffgeerling.com/blog/2022/docker-and-systemd-getting-rid-dreaded-failed-connect-bus-error)
