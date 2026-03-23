# k8s_node_roles

## Purpose

Apply K8s node labels/taints that encode node role policy in the fabric.

## Inputs

- `k8s_node_roles_kubectl_bin`
- `k8s_node_roles_edge_taint_enabled`

Full defaults: `defaults/main.yml`.

## Behavior

- Reconciles expected labels/taints on nodes from inventory grouping.
- Supports edge scheduling policy through deterministic taint settings.
- Emits cluster-side status for auditability.

## Validation

- `kubectl get nodes --show-labels`
- `kubectl describe node <node-name> | sed -n '/Taints/,+4p'`
