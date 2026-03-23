# k3s

Converges an existing K3s installation by rendering the node config and
restarting the appropriate service only when the rendered configuration changes.

## Scope
- existing `k3s` and `k3s-agent` systemd units
- server and agent nodes
- optional promotion of an existing `k3s-agent` host into a `k3s` server unit
- optional reconciliation of the `k3s-agent` unit file to `ExecStart=<k3s binary> agent`
- no fresh bootstrap logic

## Inputs
- `k3s_role`: `server` or `agent`
- `k3s_token`
- `k3s_node_ip`
- `k3s_server_advertise_address` on server nodes

## Secrets encryption
- `k3s_secrets_encryption_enabled`
- `k3s_secrets_encryption_provider`

The role can render `secrets-encryption: true` for clusters that are created
with K3s secrets encryption from the start, or for clusters where encryption is
already enabled.

When a secondary server joins a cluster with secrets encryption already enabled,
the role also synchronizes the primary server encryption state files before
starting the local `k3s` server unit.

It must not be used as proof that a running cluster created without secrets
encryption can be switched live safely. That migration remains a dedicated
maintenance topic outside the role itself.
