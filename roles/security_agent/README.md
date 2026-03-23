# security_agent

## Purpose

Operational security wrapper for Debian hosts and OpenWrt edges.

## Inputs

- `security_agent_action` (required at runtime)
- `security_agent_ssh_dropin_path`
- `security_agent_ssh_allow_users`
- `security_agent_firewall_allowed_ports` (for firewall actions)

Full defaults: `defaults/main.yml`.

## Supported actions

- `audit_security`
- `harden_ssh`
- `configure_ssh`
- `configure_firewall`
- `update_firewall_rules`
- `list_firewall_rules`
- `apply_security_baseline`
- `audit_apparmor`
- `configure_openwrt_security`
- `update_openwrt_firewall`

## Behavior

- Dispatches to host hardening roles (`host_security`, `openwrt_security`) when requested.
- Provides read-only audit outputs for SSH/AppArmor/firewall/fail2ban state.
- Fails fast on unsupported action values.

## Validation

- `ansible-playbook -i inventory/hosts.yml playbooks/agents/security-agent.yml -e "security_agent_action=audit_security"`
