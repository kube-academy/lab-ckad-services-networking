
## Setup

Apply the deployment named `cara`:

```terminal:execute
command: k apply -f services-and-networking/cara.yaml
```

## Challenge

Expose the deployment (which is running on port 8080) using a NodePort type service named `cara` using the service port 31888.

```examiner:execute-test
name: svc-cara-nodeport
title: Is deployment exposed via NodePort on port 31888?
autostart: true
```

<div style="margin-top: 5em;"></div>

```section:begin
title: Solution
```

```bash
k create svc nodeport cara --tcp=8080:8080 --node-port=31888
```

```section:end
```
