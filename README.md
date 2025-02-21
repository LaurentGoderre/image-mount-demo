# Docker Image Mount Demos

This repo contains some example usage of the image mount feature in the moby engine.

## Getting Started

The image mount feature is introduced as an experimental feature in version 28 of the moby engine.
If your local version of the engine is lower than v28 you can use the Docker-in-Docker (DinD) image
to run these examples.

The following commands will create a DinD container.

```shell
docker run \
  --rm --privileged -d \
  --name dind \
  -p 2376:2376 \
  -p 2345:2345 \
  -e DOCKER_TLS_CERTDIR=/certs \
  -v ${HOME}/.docker/local/certs/:/certs/client \
  docker:28-dind \
    --feature=containerd-snapshotter \
    --storage-driver=overlayfs
```

* Port 2376 is used for the Docker engine and port 2345 is used for the distroless debug example.

The following configures the Docker CLI in the current shell to use the Docker engine in the DinD container 
instead of the engine on the host.

```shell
export DOCKER_TLS_VERIFY=1
export DOCKER_CERT_PATH=${HOME}/.docker/local/certs
export DOCKER_HOST=tcp://localhost:2376
export DOCKER_API_VERSION=1.48
```