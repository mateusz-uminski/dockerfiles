# dockerfiles

This repository serves as a central location for storing custom Dockerfiles used for learning and exploring innovative ideas.

Besides the README.md further documentation can be found in commits, code comments and nested README files.

Feel free to explore and copy everything you want. Enjoy!


# How to use?
```sh
# build an image from local
docker build -t nginx-distroless nginx-distroless/

# build an image from a remote branch
export DOCKER_BUILDKIT=0
export COMPOSE_DOCKER_CLI_BUILD=0
docker build -t nginx-distroless github.com/mateusz-uminski/dockerfiles#main:nginx-distroless

# build an image from a specific version
docker build -t nginx-distroless github.com/mateusz-uminski/dockerfiles#nginx-distroless/v0.1.0:nginx-distroless
```
