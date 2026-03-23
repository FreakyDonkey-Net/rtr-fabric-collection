# k8s_network_services

## Purpose

Deploy and maintain in-cluster network services (DNS, RADIUS, LDAP, internal CA).

## Inputs

Core:

- `k8s_network_services_namespace`
- `k8s_network_services_kubectl_bin`
- `k8s_network_services_dry_run`

Service toggles:

- `k8s_network_services_dns_enabled`
- `k8s_network_services_radius_enabled`
- `k8s_network_services_ldap_enabled`
- `k8s_network_services_ca_enabled`

Sensitive inputs (production expected from OpenBao lookup path):

- `k8s_network_services_radius_clients[*].secret`
- `k8s_network_services_radius_users[*].password`
- `k8s_network_services_ldap_admin_password`
- `k8s_network_services_ca_password`
- TLS PEM assets when custom mode is enabled

Full defaults: `defaults/main.yml`.

## Behavior

- Validates each enabled component before rendering manifests.
- Builds derived payloads for DNS records and RADIUS configs.
- Applies Kubernetes manifests and performs targeted rollouts/checks.
- Enforces explicit hostNetwork exceptions in production.

## Validation

- `kubectl -n net-services get pods,svc`
- `kubectl -n net-services get cm,secret`
- `kubectl -n net-services logs deploy/infra-radius --tail=50` (when RADIUS enabled)
