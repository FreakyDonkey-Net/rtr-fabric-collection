# k8s_public_proxy

## Purpose

Deploy the public ingress controller (ingress-nginx class `public`) in Kubernetes.

## Inputs

- `k8s_public_proxy_namespace`
- `k8s_public_proxy_ingress_class_name`
- `k8s_public_proxy_image`
- `k8s_public_proxy_replicas`
- `k8s_public_proxy_http_port`, `k8s_public_proxy_https_port`
- security context/capabilities defaults from `defaults/main.yml`

Full defaults: `defaults/main.yml`.

## Behavior

- Creates namespace and controller resources.
- Applies hardened pod/container security defaults.
- Reconciles deployment strategy (`maxSurge`, `maxUnavailable`) and service ports.

## Validation

- `kubectl -n ingress-public get pods,svc,deploy`
- `kubectl get ingressclass public`
