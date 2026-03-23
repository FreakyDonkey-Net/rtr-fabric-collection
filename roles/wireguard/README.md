# wireguard

## Purpose

Configure WireGuard host interface, keys, and peers from inventory.

## Inputs

- `wireguard_enabled`
- `wireguard_interface`, `wireguard_group`
- `wireguard_address`, `wireguard_listen_port`
- `wireguard_disable_host_interface` (default: `true`)
- `wireguard_remove_host_interface_when_disabled`
- `wireguard_include_external_peers`

Full defaults: `defaults/main.yml`.

## Behavior

- Ensures WireGuard package and config directory.
- Generates private/public keys when absent.
- Builds peer model from inventory hostvars.
- Renders interface config and reconciles live interface when enabled.
- Supports controlled disable/removal of legacy host interface.

## Validation

- `wg show`
- `ip -brief link show type wireguard`
- `systemctl status wg-quick@wg0`

## Notes

- Key material tasks are marked `no_log`.
- Keep external peer secrets/passwords sourced from OpenBao-backed vars.
