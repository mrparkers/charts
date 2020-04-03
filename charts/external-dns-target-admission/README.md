# external-dns-target-admission

This is a mutating admission webhook that automatically adds the `external-dns.alpha.kubernetes.io/target` annotation
to `Ingress` and Istio `Gateway` resources. This allows [ExternalDNS](https://github.com/kubernetes-sigs/external-dns)
to create A records for a specific IP address in environments where it cannot otherwise be inferred, such as on-prem
deployments of Kubernetes that can't use the `LoadBalancer` service tyoe.

For more information, see the original repository: [mrparkers/external-dns-target-admission](https://github.com/mrparkers/external-dns-target-admission)

## Prerequisites:

- Kubernetes v1.13+
- [cert-manager](https://github.com/jetstack/cert-manager) (I personally use `v0.14.1`)

## Installation

The chart can be customized using the following parameters:

| Parameter          | Description                              | Default                                   |
|--------------------|------------------------------------------|-------------------------------------------|
| `image.repository` | The image to deploy                      | `mrparkers/external-dns-target-admission` |
| `image.tag`        | The version of the image to deploy       | `v0.1.0`                                  |
| `image.pullPolicy` | The `imagePullPolicy`                    | `IfNotPresent`                            |                                           |
| `ipAddress`        | The IP address to use for the annotation | `127.0.0.1`                               |                                           |
