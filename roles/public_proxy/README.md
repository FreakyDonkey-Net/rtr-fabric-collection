# public_proxy

## Purpose

Configure host-level HAProxy public proxy, including optional K3s API forwarding.

## Inputs

- `public_proxy_enabled`
- `public_proxy_dry_run`
- `public_proxy_expose_public_ports`
- `public_proxy_package_name`, `public_proxy_service_name`
- `public_proxy_k3s_api_enabled`
- `public_proxy_k3s_api_bind_host`, `public_proxy_k3s_api_bind_port`
- `public_proxy_k3s_api_backend_port`

Full defaults: `defaults/main.yml`.

## Behavior

- Installs/configures HAProxy with fabric-specific frontend/backends.
- Can keep bindings loopback-only or expose public listener ports.
- Supports optional proxying of K3s API endpoint.

## Validation

- `systemctl status haproxy`
- `ss -ltnp | grep -E '16443|8404'`
