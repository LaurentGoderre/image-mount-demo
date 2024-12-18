FROM golang:1.23-alpine AS build

COPY src /src

RUN set -ex; \
    mkdir /out; \
    cd /src; \
    go build -o /out/myapp .

FROM scratch

COPY --from=build /out/myapp /myapp

CMD ["/myapp"]