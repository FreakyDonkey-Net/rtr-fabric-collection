# openvswitch_ovn

## Purpose

Prepare host Open vSwitch/OVN service state for Kube-OVN compatibility.

## Inputs

- `openvswitch_ovn_conflicting_services`
- `openvswitch_ovn_ensure_services`

Full defaults: `defaults/main.yml`.

## Behavior

- Stops/disables host services that conflict with kube-managed OVS/OVN flows.
- Ensures required OVN host services are present/enabled.
- Keeps host service state consistent before/after Kube-OVN rollout.

## Validation

- `systemctl is-enabled ovn-host.service`
- `systemctl status ovn-host.service`
