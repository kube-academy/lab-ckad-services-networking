
1. Create a ClusterIP service for pod ``ig-11``{{copy}} named ``greet``{{copy}}. Map service port 8080 to container port 8080.

```examiner:execute-test
name: svc-clusterip-greet
title: ClusterIP service exposes pod ig-11 on port 8080?
autostart: true
```

<div style="margin-top: 5em;"></div>

```section:begin
title: Solution
```

```bash
k expose pod ig-11 --port=8080 --target-port=8080 --name=greet
```

```section:end
```
