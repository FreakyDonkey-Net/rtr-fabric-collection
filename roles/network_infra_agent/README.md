# network_infra_agent

## Purpose

Read-only network inventory checks for VLANs, interfaces, routes, and reachability.

## Inputs

- `network_infra_agent_action` (supported values in `network_infra_agent_supported_actions`)
- `network_infra_agent_ping_count` (default: `2`)

Full defaults: `defaults/main.yml`.

## Supported actions

- `list_vlans`
- `verify_interfaces`
- `verify_connectivity`
- `list_routes`

## Behavior

- Runs diagnostics on target hosts.
- Returns structured debug output for operational triage.
- Does not change host or network configuration.

## Validation

- `ansible-playbook -i inventory/hosts.yml playbooks/agents/network-infra-agent.yml -e "network_infra_agent_action=list_vlans"`
