# common

## Purpose

Shared host-level common tasks used by platform playbooks.

## Inputs

- `common_dhcpcd_override_path`

Full defaults: `defaults/main.yml`.

## Behavior

- Applies baseline network/client override files used by the platform stack.
- Keeps idempotent host preparation logic centralized for reuse.

## Validation

- Verify rendered file at `{{ common_dhcpcd_override_path }}`.
