# Ansible Collection - freakydonkey.rtr_fabric

[![Galaxy](https://img.shields.io/badge/galaxy-freakydonkey.rtr__fabric-blue.svg)](https://galaxy.ansible.com/freakydonkey/rtr_fabric)

Unified Ansible collection for RTR Fabric infrastructure management.

## Description

This collection provides Ansible roles for managing:
- **Platform**: K3s, Kube-OVN, observability, storage (Longhorn)
- **Networking**: WireGuard, BGP/EVPN, underlay VLANs
- **Security**: Host hardening, firewall, SSH configuration
- **OpenWrt Edge**: Edge router configuration (WireGuard, FRR, VLANs, WiFi)

## Installation

### From Ansible Galaxy

```bash
ansible-galaxy collection install freakydonkey.rtr_fabric
```

### From requirements.yml

```yaml
collections:
  - name: freakydonkey.rtr_fabric
    version: ">=1.0.0"
```

Then install with:
```bash
ansible-galaxy collection install -r requirements.yml
```

## Roles

### Platform (18 roles)

- `common` — Baseline OS configuration
- `k3s` — K3s server/agent deployment
- `k8s_agent` — Kubernetes agent operations
- `k8s_enterprise_security` — Enterprise security hardening for Kubernetes
- `k8s_node_roles` — Node labels and taints management
- `k8s_public_proxy` — Public ingress/proxy configuration
- `k8s_network_services` — DNS, RADIUS, LDAP, CA services
- `k8s_openbao` — OpenBao runtime and LDAP auth
- `k8s_gitops_secret_bridge` — Secret projection to GitOps namespaces
- `k8s_github_actions_runner` — GitHub Actions ARC runners
- `k8s_longhorn` — Longhorn distributed storage
- `kube_ovn` — Kube-OVN CNI overlay
- `observability_agent` — Observability verification agent
- `openvswitch_ovn` — OVS/OVN host setup
- `ovn_ssh_tunnel` — OVN database tunneling
- `public_proxy` — HAProxy host configuration
- `rpi_longhorn_storage` — Longhorn disk preparation for RPi workers
- `edge_worker_prep` — Edge/RPi worker preparation

### Network Edge (6 roles)

- `bgp_agent` — BGP/EVPN agent operations
- `k8s_bgp_evpn` — BGP/EVPN manifests for Kubernetes
- `kube_ovn_underlay` — Underlay VLAN configuration
- `network_infra_agent` — Network infrastructure agent
- `wireguard` — WireGuard host tunneling
- `wireguard_agent` — WireGuard agent operations

### Security (2 roles)

- `host_security` — Debian host hardening
- `security_agent` — Security agent operations

### OpenWrt Edge (6 roles)

- `openwrt_edge` — OpenWrt edge router (WireGuard + FRR)
- `openwrt_dns_forwarders` — Dnsmasq upstreams/rebind configuration
- `openwrt_mdns_reflector` — Avahi mDNS reflector inter-VLAN
- `openwrt_security` — OpenWrt security hardening
- `openwrt_site_vlans` — Site VLAN configuration
- `openwrt_wifi_profiles` — SSID/VLAN WiFi profiles

## Usage

Use roles with their Fully Qualified Collection Name (FQCN):

```yaml
- name: Deploy K3s cluster
  hosts: k3s_servers
  roles:
    - role: freakydonkey.rtr_fabric.k3s
      vars:
        k3s_role: server

- name: Configure WireGuard tunnels
  hosts: wireguard_hosts
  roles:
    - freakydonkey.rtr_fabric.wireguard
```

## Migration from Split Collections

This collection unifies 4 previous collections:
- `rtr-fabric-collection-platform`
- `rtr-fabric-collection-network-edge`
- `rtr-fabric-collection-openwrt-edge`
- `rtr-fabric-collection-security`

Old collections are archived and read-only. Please migrate to this unified collection.

## License

GPL-3.0-or-later

## Author

FreakyDonkey-Net

## Links

- [GitHub Repository](https://github.com/FreakyDonkey-Net/rtr-fabric-collection)
- [Main Project](https://github.com/FreakyDonkey-Net/rtr-fabric)
- [Issues](https://github.com/FreakyDonkey-Net/rtr-fabric-collection/issues)
