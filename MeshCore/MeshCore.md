---
title: MeshCore
description: Introduction to MeshCore in the Scottish Mesh community.
published: false
date: 2026-05-31T18:04:19.360Z
tags: meshcore, scotland
editor: markdown
dateCreated: 2026-04-24T13:26:05.328Z
---

# Meshes

ScotMesh has both Meshtastic and  MeshCore — radio messaging systems for small LoRa devices. It lets people send short messages across a volunteer-run network without needing mobile coverage, Wi-Fi, or the internet. Carry a small companion node in your pocket, connect it to your phone, and you're on the mesh.

# The remainder of this dsocument focuses on Meshcore.

## 💡 Key ideas

| Term | Meaning |
|---|---|
| **Channel** | A named place for conversation, such as `#scotland`, `#glasgow`, or `#ireland`. |
| **Scope** | The region code applied to messages in a channel, such as `sco`, `gla`, or `ioi`. |
| **Region** | A code configured on a repeater to describe the area it serves. |
| **Repeater** | A fixed node that hears MeshCore traffic and repeats it to extend coverage. |

## 👋 New to ScotMesh?

- [Getting Started](/meshcore/getting-started) — what it is, what you need, your first message.
- [Scopes](/meshcore/scopes) — the one setting that matters most.
- [Channels](/meshcore/channels) — where to talk and what scope to use.
- [FAQ](/meshcore/faq) — quick answers to common questions.

## 📡 Setting up a repeater?

- [Repeater Quick Setup](/meshcore/repeater-quick-setup) — start here for hardware and commands.
- [Regions](/meshcore/regions) — full region code reference and configuration policy.
- [Observers](/meshcore/observers) — MQTT map uplink setup.

## 🔧 Interested in the technical detail?

- [Region Filtering](https://blog.meshcore.io/2026/01/20/region-filtering)
- [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope)
- [CLI Commands](https://docs.meshcore.io/cli_commands/)

---

> **ScotMesh network policy:** wildcard `*` forwarding is not allowed. Companion App users should set their default region scope to `sco` under **Experimental Settings**. Repeater owners should use `region denyf *`. See [Regions](/MeshCore/regions) for detail.
{.is-warning}
