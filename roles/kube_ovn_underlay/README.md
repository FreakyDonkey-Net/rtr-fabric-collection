# kube_ovn_underlay

## Purpose

Manage Kube-OVN underlay/provider network wiring for VLAN-backed connectivity.

## Inputs

- `kube_ovn_underlay_enabled`
- `kube_ovn_underlay_autodetect`
- `kube_ovn_underlay_force_apply`
- `kube_ovn_underlay_dry_run`
- `kube_ovn_underlay_provider_network_name`
- `kube_ovn_underlay_trunk_interface_map`
- `kube_ovn_underlay_trunk_ports`
- `kube_ovn_underlay_access_ports`
- `kube_ovn_underlay_internal_ports`
- `kube_ovn_underlay_legacy_internal_ports`
- `kube_ovn_underlay_artifact_dir`

Full defaults: `defaults/main.yml`.

## Behavior

- Builds effective underlay mapping from inventory and explicit overrides.
- Can enforce explicit OVS trunk port policy (VLAN list + trunk mode) on `br-underlay-net`.
  - `vlan_mode` supports `trunk` (default), `native-tagged`, `native-untagged`.
  - Native modes require `native_vlan_id`.
- Can attach spare bare-metal NICs as local OVS access ports on `br-underlay-net`.
- Can attach local OVS internal interfaces with static IPv4 addresses on `br-underlay-net`.
- Can remove legacy internal interfaces/ports (default: `diag-admin11`, `diag-mgmt10`) and disable stale local-policy service artifacts.
- Applies provider network and subnet objects.
- Can cleanup legacy objects when `kube_ovn_underlay_cleanup_legacy=true`.
- Writes troubleshooting artifacts to `kube_ovn_underlay_artifact_dir`.

## Validation

- `kubectl -n kube-system get providernetworks.kubeovn.io`
- `kubectl -n kube-system get subnets.kubeovn.io`
