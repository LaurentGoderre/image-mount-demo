## Get started

```
docker build --build-arg BUILDKIT_SYNTAX=laurentgoderre689/buildkit-certmerge --build-arg DISTRO=debian . -f - <<< "" -t laurentgoderre689/certs:debian --push
docker compose up
```
