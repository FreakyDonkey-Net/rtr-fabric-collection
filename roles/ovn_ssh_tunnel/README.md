# ovn_ssh_tunnel

## Purpose

Manage a persistent SSH local-forward tunnel to remote OVN DB endpoints.

## Inputs

- `ovn_ssh_tunnel_enabled` (default: `false`)
- `ovn_ssh_tunnel_unit_name`
- `ovn_ssh_tunnel_user`, `ovn_ssh_tunnel_group`
- `ovn_ssh_tunnel_ssh_key_path`
- `ovn_ssh_tunnel_remote_user`, `ovn_ssh_tunnel_remote_host`
- `ovn_ssh_tunnel_ports`

Full defaults: `defaults/main.yml`.

## Behavior

- Renders a systemd unit for SSH tunnel persistence.
- Enables/starts or disables/stops tunnel service based on `enabled`.
- Uses keepalive settings to reduce silent tunnel drift.

## Validation

- `systemctl status ovn-db-tunnel.service`
- `ss -ltnp | grep -E '6641|6642'`
