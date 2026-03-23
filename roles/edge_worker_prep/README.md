# edge_worker_prep

## Purpose

Prepare edge worker hosts (notably Raspberry Pi) for network attachment and K3s prerequisites.

## Inputs

Network Manager trunk workflow:

- `edge_worker_prep_nm_trunk_enabled`
- `edge_worker_prep_nm_parent_iface`
- `edge_worker_prep_nm_vlan_iface`
- `edge_worker_prep_nm_vlan_id`
- `edge_worker_prep_nm_vlan_ip4`, `edge_worker_prep_nm_vlan_gw4`, `edge_worker_prep_nm_vlan_dns4`

Static interface / dhcpcd guardrail workflow:

- `edge_worker_prep_dhcpcd_deny_interfaces`
- `edge_worker_prep_dhcpcd_config_path`
- `edge_worker_prep_ifupdown_takeover_unmanaged` (allow first takeover of non-managed `/etc/network/interfaces`)

Automation sudo workflow:

- `edge_worker_prep_sudo_nopasswd_enabled`
- `edge_worker_prep_sudo_nopasswd_user`
- `edge_worker_prep_sudo_nopasswd_file`

K3s preflight workflow:

- `edge_worker_prep_k3s_preflight_enabled`
- `edge_worker_prep_k3s_required_cmdline_tokens`
- `edge_worker_prep_k3s_fail_if_memory_controller_missing`
- `edge_worker_prep_k3s_fail_if_swap_present`

Full defaults: `defaults/main.yml`.

## Behavior

- Optionally applies/administers VLAN trunk NM profile.
- Optionally writes `denyinterfaces` entries to `dhcpcd.conf` for statically managed interfaces.
- Optionally installs a validated `sudoers.d` rule for the automation user.
- Runs kernel/cgroup/swap preflight checks required for stable K3s operation.
- Supports breakglass Wi-Fi profile handling via configured connection names.

## Validation

- `nmcli connection show`
- `grep '^denyinterfaces ' /etc/dhcpcd.conf`
- `visudo -cf /etc/sudoers.d/...`
- `cat /boot/firmware/cmdline.txt`
- `swapon --noheadings --raw`
