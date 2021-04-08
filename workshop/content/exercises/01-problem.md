
1. Create a pod named ``ig-11``{{copy}} with image ``bitnami/nginx``{{copy}} and specifying the container port 8080.

```examiner:execute-test
name: svc-pod-ig11
title: Pod ig-11 running, specifies container port 8080?
autostart: true
```

<div style="margin-top: 5em;"></div>

```section:begin
title: Solution
```

```bash
k run ig-11 --image=bitnami/nginx --port=8080
```

```section:end
```
