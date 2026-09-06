# AGENTS.md

Instructions for AI agents (Codex, Claude Code via its `CLAUDE.md` symlink to
this file, or any other agent) working in this repository.

## What This Repository Is

A fork of the upstream open-source brewing/fermentation controller
[craftbeerpi/craftbeerpi4](https://github.com/craftbeerpi/craftbeerpi4)
(`origin` is `Adamp457/craftbeerpi4`, `upstream` is the real project). Git
history here is almost entirely upstream merge commits — this is **vendored
code, not homelab-authored software**. Treat it accordingly:

- Don't invent local architecture docs that duplicate upstream's own
  documentation at [gitbook.io](https://openbrewing.gitbook.io/craftbeerpi4_support/).
- Prefer pulling and merging from `upstream` over hand-patching vendored files,
  so any real local deviation stays visible as a merge conflict rather than a
  silent divergence.
- If a change is homelab-specific (not something to send upstream), keep it
  small and say so in the commit message — anything else should look like it
  could be a PR to `craftbeerpi/craftbeerpi4`.

## Deployment

Runs on a Raspberry Pi via the packaged systemd unit (`craftbeerpi.service`,
`ExecStart=/usr/local/bin/cbpi start`) — **not** in Docker, and not part of
`docker-homelab/`. The `.devcontainer/` setup is for developing the app itself
in VS Code, not how it runs in production here.

## Integration with the rest of the homelab

CraftBeerPi publishes brewing sensor data over MQTT, which
`HomeAssistantConfig/mqtt.yaml` reads ("CraftBeerPi brewing sensors") — see
`HomeAssistantConfig/SENSORS.md` §6 for the documented mapping. That's the
only coupling to the rest of this workspace; don't assume any other repo
here depends on this one.
