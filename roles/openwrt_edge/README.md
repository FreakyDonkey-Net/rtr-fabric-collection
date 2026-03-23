# openwrt_edge

Converges external OpenWrt edge routing state:

- WireGuard uplinks towards route-reflectors
- loopback-based eBGP with FRR (or BIRD legacy backend)
- optional OSPF underlay for edge uplinks (disabled by default, unicast neighbors over WireGuard)
- static `/32` routes required for tunnel and loopback reachability
- runtime facts consumed by the orchestrator for external EVPN peers

The role is designed to stay aligned with:

- `inventory/host_vars/*` edge uplink definitions
- `playbooks/cluster/45-external-edges.yml`
- `playbooks/ops/99-verify.yml`
