# kube_ovn

## Purpose

Operate Kube-OVN control-plane/data-plane rollout and convergence checks.

## Inputs

- `kube_ovn_namespace`
- `kube_ovn_kubectl_bin`
- `kube_ovn_controller_deployment_name`
- `kube_ovn_cni_daemonset_name`
- `kube_ovn_ovs_daemonset_name`
- `kube_ovn_rollout_timeout`
- `kube_ovn_expected_daemonsets`, `kube_ovn_expected_deployments`

Full defaults: `defaults/main.yml`.

## Behavior

- Checks component readiness in the target namespace.
- Executes rollout/wait logic for OVN controller/CNI/OVS components.
- Fails with explicit diagnostics when expected components are missing/unready.

## Validation

- `kubectl -n kube-system get ds,deploy | grep -E 'kube-ovn|ovn'`
- `kubectl -n kube-system rollout status deploy/kube-ovn-controller`
