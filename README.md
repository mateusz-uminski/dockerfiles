# dockerfiles

[![build](https://github.com/mateusz-uminski/dockerfiles/actions/workflows/build.yaml/badge.svg)](https://github.com/mateusz-uminski/dockerfiles/actions/workflows/build.yaml)

This repository serves as a collection of Dockerfiles specifically designed to build base images that can be used in other projects. These Dockerfiles are used for learning and verifying unconventional ideas.

Besides the README.md further documentation can be found in commits, code comments and nested README files.

Feel free to explore and copy everything you want. Enjoy!

# Usage
```sh
# build an image from a local environment
cd $(git rev-parse --show-toplevel)
docker build -t <image name>:<tag> <path to a dockerfile>/

# build an image from a remote
export DOCKER_BUILDKIT=0
export COMPOSE_DOCKER_CLI_BUILD=0
docker build -t <image name>:<tag> github.com/mateusz-uminski/dockerfiles#main:<path to a dockerfile>
```
