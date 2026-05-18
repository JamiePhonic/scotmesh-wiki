---
title: MeshCore
description: Introduction to MeshCore in the Scottish Mesh community.
published: true
date: 2026-05-18T23:41:00.000Z
tags: meshcore, scotland
editor: markdown
dateCreated: 2026-04-24T13:26:05.328Z
---

# MeshCore

MeshCore is a radio messaging system for small LoRa devices. It lets people send short messages through nearby radios and repeaters without relying on mobile phone coverage, Wi-Fi, or the internet.

For ScotMesh, that means local, regional, and Scotland-wide communication can keep working across a volunteer-run network. You might carry a small companion node connected to your phone, while fixed repeaters in useful locations help messages travel further.

## Key ideas

| Term | Meaning |
|---|---|
| **Channel** | A named place for conversation, such as `#scotland`, `#glasgow`, or `#ireland`. |
| **Scope** | The region code applied to messages in a channel, such as `sco`, `gla`, or `ioi`. |
| **Region** | A code configured on a repeater to describe the area it serves. |
| **Repeater** | A fixed node that hears MeshCore traffic and repeats it to extend coverage. |

## New to ScotMesh?

- [Getting Started](getting-started) — what it is, what you need, your first message.
- [Scopes](scopes) — the one setting that matters most.
- [Channels](channels) — where to talk and what scope to use.

## Setting up a repeater?

- [Repeater Quick Setup](repeater-quick-setup) — start here for hardware and commands.
- [Regions](regions) — full region code reference and configuration policy.
- [Observers](observers) — MQTT map uplink setup.

## Interested in the technical detail?

- [Region Filtering](https://blog.meshcore.io/2026/01/20/region-filtering)
- [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope)
- [CLI Commands](https://docs.meshcore.io/cli_commands/)

---

> **ScotMesh network policy:** wildcard `*` forwarding is not allowed. Companion App users should set their default region scope to `sco` under **Experimental Settings**. Repeater owners should use `region denyf *`. See [Regions](regions) for detail.
{.is-warning}
