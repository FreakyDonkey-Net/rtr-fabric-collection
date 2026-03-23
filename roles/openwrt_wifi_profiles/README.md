# openwrt_wifi_profiles

Converges managed Wi-Fi SSIDs on OpenWrt edges:

- `trusted` on VLAN `users`
- `admin` on VLAN `admin`
- `iot` on VLAN `guest`

The role supports:

- PSK-based SSIDs
- WPA-Enterprise on `trusted` with RADIUS
- cleanup of legacy iface sections
- idempotent UCI convergence with optional dry-run
