# k8s_bgp_evpn

## Purpose

Apply and verify K8s-side BGP EVPN configuration used by the network fabric.

## Inputs

- `k8s_bgp_evpn_enabled`
- `k8s_bgp_evpn_namespace`
- `k8s_bgp_evpn_kubectl_bin`
- `k8s_bgp_evpn_external_peers`
- `k8s_bgp_evpn_external_gateway_proxy_prefixes`
- `k8s_bgp_evpn_internal_peer_extra_prefixes`
- `k8s_bgp_evpn_verify_pods`, `k8s_bgp_evpn_verify_bgp`

Full defaults: `defaults/main.yml`.

## Behavior

- Renders/applies EVPN-related objects in the target namespace.
- Supports restart/wait control lists for targeted rollouts.
- Can verify pod readiness and BGP convergence post-apply.

## Validation

- `kubectl -n fabric-net get pods`
- `kubectl -n fabric-net get cm,ds,deploy | grep -i bgp`

## Notes

- Keep peer/password data sourced from OpenBao-backed variables in production.
