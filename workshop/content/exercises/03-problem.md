
1. Expose the greet service to the outside world via an [ingress resource](https://kubernetes.io/docs/concepts/services-networking/ingress/).
  Use [name-based virtual hosting](https://kubernetes.io/docs/concepts/services-networking/ingress/#name-based-virtual-hosting).
  Name the ingress `greet-ingress`. Set the `host` to `{{session-namespace}}-greet.{{ingress_domain}}`.  The ingress backend should map to your internal `greet` ClusterIP service running on port 8080.

```examiner:execute-test
name: svc-greet-ingress
title: Is deployment exposed via NodePort on port 31888?
autostart: true
```

<div style="margin-top: 5em;"></div>

```section:begin
title: Solution
```

1. Draft an ingress specification with the specified parameters, as follows (to a file named, say, `ingress.yaml`).

    ```yaml
    ---
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: greet-ingress
    spec:
      rules:
      - host: {{session_namespace}}-greet.{{ingress_domain}}
        http:
          paths:
          - pathType: Prefix
            path: "/"
            backend:
              service:
                name: greet
                port:
                  number: 8080
    ```

1. Apply the resource.

    ```bash
    k apply -f ingress.yaml
    ```

```section:end
```
