FROM golang:1.20-bullseye AS build

ENV JSONNET_VERSION=v0.19.1

WORKDIR /jsonnet

RUN git clone https://github.com/google/go-jsonnet \
    && cd go-jsonnet \
    && git checkout ${JSONNET_VERSION} \
    && make build

FROM debian:bullseye-slim

COPY --from=build /jsonnet/go-jsonnet/jsonnet /usr/local/bin/jsonnet

ENV JB_VERSION=v0.6.0

# dependencies
RUN apt-get update \
    && apt-get install --no-install-recommends -y curl ca-certificates \
    # reduce size of the image
    && apt-get autoremove --purge -y \
    && rm -rf /var/lib/apt/lists/ /var/cache/apt/ /usr/share/doc /usr/share/man

# bundler
RUN arch=$(arch) && \
    # map arch
    if [ $arch = "x86_64" ]; then \
        arch="linux-amd64"; \
    elif [ $arch = "aarch64" ]; then \
        arch="linux-arm64"; \
    fi \
    && curl -L \
        https://github.com/jsonnet-bundler/jsonnet-bundler/releases/download/${JB_VERSION}/jb-${arch} \
        -o /usr/local/bin/jb \
    && chmod +x /usr/local/bin/jb
