# k8s_agent

## Purpose

Run day-2 Kubernetes operations against the K3s cluster.

## Inputs

- `k8s_agent_action` (must be one of `k8s_agent_supported_actions`)

Supported actions:

- `check_k3s_status`
- `label_node`
- `taint_node`
- `drain_node`
- `etcd_snapshot`

Full defaults: `defaults/main.yml`.

## Behavior

- Normalizes/validates requested action.
- Executes operational kubectl/k3s commands for targeted cluster maintenance.
- Returns explicit diagnostics on failure paths.

## Validation

- `ansible-playbook -i inventory/hosts.yml playbooks/agents/k8s-agent.yml -e "k8s_agent_action=check_k3s_status"`
