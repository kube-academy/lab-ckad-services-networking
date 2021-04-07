
## Setup

1. Apply the pod `geonosis`:

    ```terminal:execute
    command: k apply -f services-and-networking/geonosis-pod.yaml
    ```

1. Apply the accompanying ClusterIP service by the same name:

    ```terminal:execute
    command: k apply -f services-and-networking/geonosis-svc.yaml
    ```

## Challenge

Create a network policy `geonosis-shield` which allows only pods with the label `empire=true` to access the service. Use appropriate labels.

```examiner:execute-test
name: svc-geonosis-netpol
title: Is network policy in place for the geonosis service?
autostart: true
```

<div style="margin-top: 5em;"></div>

```section:begin
title: Solution
```

1. Review the documentation on the subject of [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/);

1. Draft a network policy spec (in a file named, say, `netpol.yaml`), as follows:

    ```yaml
    ---
    apiVersion: networking.k8s.io/v1
    kind: NetworkPolicy
    metadata:
      name: geonosis-shield
    spec:
      podSelector:
        matchLabels:
          sector: arkanis
      ingress:
      - from:
        - podSelector:
            matchLabels:
              empire: "true"
    ```

1. Apply the network policy (`k apply -f netpol.yaml`)

```section:end
```
