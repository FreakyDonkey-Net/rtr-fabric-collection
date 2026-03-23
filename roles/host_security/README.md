# host_security

Role de baseline securite pour les hôtes Debian.

Perimetre:
- sysctl hardening safe
- fail2ban pour `sshd`
- firewall `nftables` (dry-run par defaut)
- AppArmor (audit, service, utilitaires, activation boot optionnelle)

Points importants:
- `host_security_firewall_dry_run=true` par defaut
- `host_security_apparmor_manage_cmdline=true` seulement sur les hôtes ou un reboot est accepte
- OpenWrt est hors perimetre de ce role
