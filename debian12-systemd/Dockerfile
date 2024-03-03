FROM debian:bookworm

RUN apt-get update \
    && apt-get install --no-install-recommends -y systemd systemd-sysv \
        python-is-python3 sudo iproute2 ca-certificates procps gnupg \
    # do not run additional systemd services
    && rm -rf /etc/systemd/system/*.wants/* \
    && rm -rf /lib/systemd/system/local-fs.target.wants/* \
    && rm -rf /lib/systemd/system/multi-user.target.wants/* \
    && rm -rf /lib/systemd/system/sockets.target.wants/*initctl* \
    && rm -rf /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles* \
    && rm -rf /lib/systemd/system/systemd-update-utmp* \
    # slimming
    && apt-get autoremove --purge -y \
    && rm -rf /var/lib/apt/lists/ /var/cache/apt/ /usr/share/doc /usr/share/man

ENTRYPOINT ["/lib/systemd/systemd"]
