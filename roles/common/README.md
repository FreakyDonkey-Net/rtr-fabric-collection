# common

## Purpose

Shared host-level common tasks used by platform playbooks.

## Inputs

- `common_dhcpcd_override_path`
- `common_bootstrap_dhcp_enabled`
- `common_bootstrap_dhcp_interface`
- `common_bootstrap_dhcp_range_start`
- `common_bootstrap_dhcp_range_end`
- `common_bootstrap_dhcp_router`

Full defaults: `defaults/main.yml`.

## Behavior

- Applies baseline network/client override files used by the platform stack.
- Can run a small bootstrap DHCP service (dnsmasq) on selected hosts/interfaces.
- Keeps idempotent host preparation logic centralized for reuse.

## Validation

- Verify rendered file at `{{ common_dhcpcd_override_path }}`.
- When enabled, verify `{{ common_bootstrap_dhcp_config_path }}` and service status.
