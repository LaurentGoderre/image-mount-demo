## Get started

```
docker pull laurentgoderre689/delve
docker compose up -d
```

#### Debug using the CLI

```
dlv connect localhost:2345
> break main.go:8
> continue
```

#### Debug using VS Code

Use the following snip in yout launch.json

```
{
    "name": "Connect to external Go session",
    "type": "go",
    "debugAdapter": "dlv-dap", // `legacy` by default
    "request": "attach",
    "mode": "remote",
    "port": 2345, // 55002
    "host": "127.0.0.1", // can skip for localhost
    "substitutePath": [
        { "from": "${workspaceFolder}/image-mount-demo/distroless/src", "to": "/go/src/github.com/laurentgoderre/myapp" },
    ],
},
```
