FROM debian:bullseye-slim AS base

RUN apt-get update \
    && apt-get install --no-install-recommends -y curl lsb-release ca-certificates \
    # install helper tools
    && apt-get install --no-install-recommends -y procps vim netcat tcpdump \
        net-tools iputils-ping traceroute \
    # add deb repository
    && FRR_GPG_KEY="/usr/share/keyrings/frrouting.gpg" \
    && FRR_URI="https://deb.frrouting.org/frr" \
    && FRR_COMPONENTS="$(lsb_release -s -c) frr-9" \
    && curl -s https://deb.frrouting.org/frr/keys.gpg | tee $FRR_GPG_KEY \
    && echo "deb [signed-by=$FRR_GPG_KEY] $FRR_URI $FRR_COMPONENTS" | tee /etc/apt/sources.list.d/frr.list \
    # install frr
    && apt-get update && apt-get install --no-install-recommends -y frr \
    # configure frr
    && echo "log stdout" \
        | tee /etc/frr/zebra.conf \
        | tee /etc/frr/staticd.conf \
        | tee /etc/frr/bgpd.conf \
        | tee /etc/frr/ospfd.conf \
    && echo "no service integrated-vtysh-config" > /etc/frr/vtysh.conf \
    && chown frr:frr -R /etc/frr \
    # supervisord
    && apt-get install --no-install-recommends -y supervisor \
    # slimming
    && apt-get autoremove --purge -y \
    && rm -rf /var/lib/apt/lists/ /var/cache/apt/ /usr/share/doc /usr/share/man

COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh

COPY supervisord.conf /etc/supervisor/conf.d/test.conf

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
