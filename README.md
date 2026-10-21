# Rotom Compose Configuration

This repository provides version history and an off-site copy of the current,
non-secret Docker Compose deployment definitions for Rotom. Its working tree is
the live path `/srv/rotom/stacks`; the stack directories must not be moved,
renamed, symlinked, or restructured for Git.

## Scope

Tracked configuration is limited to the current `compose.yaml` definitions in
these service domains and the non-secret deployment-support files required by
their stacks:

- `platform`
- `libraries`
- `hosted-websites`
- `game-servers`
- `smart-home`

Secrets, `.env` files, `/srv/rotom/secrets`, `/srv/rotom/appdata`, Docker
volumes, databases, logs, certificates, NAS data, generated output, Git
internals, and historical `*.before-*` copies are deliberately excluded. A
reference to an external secret is not a reason to copy that secret here.

## Validation and recovery

Validate every affected project with `docker compose -f PATH/compose.yaml
config -q` before committing and again after applying an intended service
change. Introducing or updating this repository does not itself authorize a
container restart or recreation.

This repository supplements but does not replace Rotom Restic, the Proxmox VM
backup, NAS protection, or Rotom Support (RS). Use RS for the authoritative
operational, recovery, and safety procedures.

## Operating labels

- **Update Rotom Compose** — edit a tracked file in `/srv/rotom/stacks`,
  validate the affected project, inspect the diff, commit and push, then apply
  only the intended targeted service change.
- **Update RS** — document verified changes to live contracts, procedures,
  recovery guidance, security boundaries, ports, paths, ownership, backup
  scope, or service behavior.
- **Update Rotom Compose and RS** — use when a Compose change also changes
  RS-documented state.
