# nginx-distroless


# How to use?
```sh
# build an image from local
cd $(git rev-parse --show-toplevel)
docker build -t nginx-distroless nginx-distroless/

# build an image from a remote branch
export DOCKER_BUILDKIT=0
export COMPOSE_DOCKER_CLI_BUILD=0
docker build -t nginx-distroless github.com/mateusz-uminski/dockerfiles#main:nginx-distroless

# build an image from a specific version
export DOCKER_BUILDKIT=0
export COMPOSE_DOCKER_CLI_BUILD=0
docker build -t nginx-distroless:0.1.0 github.com/mateusz-uminski/dockerfiles#nginx-distroless/v0.1.0:nginx-distroless
```
