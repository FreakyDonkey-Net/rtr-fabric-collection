# wireguard_agent

## Purpose

Operational wrapper for WireGuard: reconcile interface config or run diagnostics.

## Inputs

- `wireguard_agent_action`
- `wireguard_agent_interface` (default: `wireguard_interface` or `wg0`)

Full defaults: `defaults/main.yml`.

## Supported actions

- `create_interface`
- `configure_interface`
- `update_config`
- `list_interfaces`
- `list_peers`
- `show_status`
- `debug_tunnel`
- `test_connection`

## Behavior

- Delegates configuration actions to role `wireguard`.
- Uses read-only commands for status/debug actions.
- Fails fast on unsupported action.

## Validation

- `ansible-playbook -i inventory/hosts.yml playbooks/agents/wireguard-agent.yml -e "wireguard_agent_action=show_status"`
