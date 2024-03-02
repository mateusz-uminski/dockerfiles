# nginx-distroless

Distroless container image of the nginx.

# Prerequisites
1. Read [Google Container Tools (distroless)](https://github.com/GoogleContainerTools/distroless)

# Usage
```sh
# building
cd $(git rev-parse --show-toplevel)
docker build -t nginx-distroless nginx-distroless/
```
