FROM almalinux:9

RUN dnf -y update \
    && dnf -y install sudo iproute procps \
    # do not run additional systemd services
    && rm -rf /etc/systemd/system/*.wants/* \
    && rm -rf /lib/systemd/system/basic.target.wants/* \
    && rm -rf /lib/systemd/system/remote-fs.target.wants/* \
    && rm -rf /lib/systemd/system/multi-user.target.wants/* \
    && rm -rf /lib/systemd/system/sockets.target.wants/*initctl* \
    && rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles* \
    && rm -rf /lib/systemd/system/systemd-update-utmp* \
    # slimming
    && dnf -y clean all \
    && rm -rf /var/cache/dnf

ENTRYPOINT ["/usr/lib/systemd/systemd"]
