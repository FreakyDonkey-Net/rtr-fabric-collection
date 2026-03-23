# bgp_agent

## Purpose

Read-only diagnostics for BGP and EVPN state from the cluster/network edge.

## Inputs

- `bgp_agent_action` (required at runtime; must be in `bgp_agent_supported_actions`)
- `bgp_agent_kubectl_bin` (default: `kubectl`)
- `bgp_agent_kubectl_namespace` (default: `fabric-net`)
- `bgp_agent_default_ping_count` (default: `2`)

Full defaults: `defaults/main.yml`.

## Behavior

- Normalizes and validates requested action.
- Runs BGP/EVPN verification commands (`kubectl`, `birdc`, ping checks).
- Emits a diagnostic summary without changing infrastructure state.

## Validation

- `ansible-playbook .../bgp-agent.yml -e "bgp_agent_action=show_bgp_status"`
- `ansible-playbook .../bgp-agent.yml -e "bgp_agent_action=verify_evpn"`

## Notes

- This role is intended for operations checks, not configuration rollout.
