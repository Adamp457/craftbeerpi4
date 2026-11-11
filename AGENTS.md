# AGENTS.md

Instructions for AI agents working in this repository (Claude Code reads it
through the `CLAUDE.md` symlink).

## What this repository is

A fork of [PiBrewing/craftbeerpi4](https://github.com/PiBrewing/craftbeerpi4),
the maintained CraftBeerPi 4 (`upstream`). `master` tracks upstream's `master`
(4.7.7 as of 2026-11-11) plus this file. This is upstream's code, not ours:

- Don't add local architecture docs that duplicate upstream's
  [documentation](https://openbrewing.gitbook.io/craftbeerpi4_support/).
- A change worth keeping goes on a branch from `upstream/development` and is
  sent upstream as a pull request. Don't patch `master`.
- The production install is the PyPI `cbpi4` package, not a build from this
  repo.

## Public repository

This fork is public. Never commit hostnames, addresses, container or VM IDs,
credentials, or anything else about the deployment. The operator keeps those in
the private `brewery` repo (`brewery/docs/system-description.md`,
`brewery/herms/rig.md`), a sibling checkout in the operator's workspace.

## Open upstream work

- `fix/close-websockets-on-shutdown`: close WebSocket clients on shutdown, so a
  stop under systemd's 30 s timeout no longer ends in SIGKILL. The same fix
  ships in the `cbpi4-heartbeat-watchdog` plugin until upstream has it.
