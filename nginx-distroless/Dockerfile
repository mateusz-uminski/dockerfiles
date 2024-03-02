FROM nginx:1.24.0-bullseye AS base
RUN arch=$(arch) \
    && mkdir -p /opt/var/cache/nginx \
    && cp -aL --parents /var/run /opt \
    && cp -a --parents /var/log/nginx /opt \
    && cp -a --parents /etc/nginx /opt \
    && cp -a --parents /etc/passwd /opt \
    && cp -a --parents /etc/group /opt \
    && cp -a --parents /usr/sbin/nginx /opt \
    && cp -a --parents /usr/sbin/nginx-debug /opt \
    && cp -a --parents /usr/share/nginx /opt \
    && cp -a --parents /usr/lib/nginx /opt \
    && cp -a --parents /usr/lib/${arch}-linux-gnu/libpcre2-8.so.* /opt \
    && cp -a --parents /lib/${arch}-linux-gnu/libcrypt.so.* /opt \
    && cp -a --parents /lib/${arch}-linux-gnu/libc.* /opt \
    && cp -a --parents /lib/${arch}-linux-gnu/libz.* /opt \
    && cp /usr/share/zoneinfo/UTC /opt/etc/localtime

# final
FROM gcr.io/distroless/base-debian11:latest
COPY --from=base /opt /
ENTRYPOINT ["/usr/sbin/nginx"]
CMD ["-g", "daemon off;"]
