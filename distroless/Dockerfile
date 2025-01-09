FROM golang:1.23-alpine AS build

COPY src /go/src/github.com/laurentgoderre/myapp

RUN set -ex; \
    mkdir /out; \
    cd /go/src/github.com/laurentgoderre/myapp/; \
    go build -o /out/myapp .

FROM scratch

COPY --from=build /out/myapp /myapp

CMD ["/myapp"]