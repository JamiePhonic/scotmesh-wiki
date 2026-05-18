---
title: MeshCore
description: Introduction to MeshCore in the Scottish Mesh community.
published: true
date: 2026-04-24T13:26:07.560Z
tags: meshcore, scotland
editor: markdown
dateCreated: 2026-04-24T13:26:05.328Z
---

# MeshCore

MeshCore is a radio messaging system for small LoRa devices. It lets people send short messages through nearby radios and repeaters without relying on mobile phone coverage, Wi-Fi, or the internet.

For ScotMesh, that means local, regional, and Scotland-wide communication can keep working across a volunteer-run network. You might carry a small companion node connected to your phone, while fixed repeaters in useful locations help messages travel further.

## Important setup notice

> The ScotMesh MeshCore network no longer accepts wildcard `*` traffic.
>
> If you use the MeshCore Companion App on our network, set your default region to `sco` under **Experimental Settings**. MeshCore calls this setting the **default scope region**. It helps ensure your messages are scoped for Scotland instead of relying on wildcard forwarding. Repeater-side detail: [Regions](regions) (IOI peering agreement).
>
> For more background, see the MeshCore blog post [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope).
{.is-warning}

## Key ideas

MeshCore uses a few terms that are worth understanding before changing settings.

| Term | Meaning |
|---|---|
| **Channel** | A named place for conversation, such as `#scotland`, `#glasgow`, or `#ireland`. |
| **Scope** | The region code applied to messages in a channel, such as `sco`, `gla`, or `ioi`. |
| **Region** | A code configured on a repeater to describe the area it serves. |
| **Repeater** | A fixed node that hears MeshCore traffic and repeats it to extend coverage. |

A channel name alone does not control where traffic travels. The important routing detail is the **scope**. For example, the `#glasgow` channel should use the `gla` scope when traffic should stay in the Glasgow area, while **`#ireland`** may use **`ioi` or `sco`** depending on whether you want the Island of Ireland scoped path or Scotland-wide scoped carriage (see [Scopes](scopes)).

## Scottish MeshCore guidance

The Scottish MeshCore network uses deliberate region-based routing. Messages should be sent with a **scope** that matches where they need to travel, and wildcard forwarding is not allowed in the Scottish setup.

## Start here

Suggested order if you are new: [Scopes](scopes) (how to set scope and avoid "shouting into the void") → [Channels](channels) (example names and scopes) → [Regions](regions) if you run or plan repeaters → [Observers](observers) if you uplink to the live map.

- [Repeater Quick Setup](repeater-quick-setup) is the easiest starting point for setting up a ScotMesh repeater.
- [Channels](channels) lists example and proposed MeshCore channels with typical scopes.
- [Regions](regions) explains the Scottish region code scheme and repeater guidance.
- [Scopes](scopes) explains how Companion App users should choose and set region scope.
- [Observers](observers) explains MQTT observer setup on repeaters (MayoMesh, firmware, `mqtt.iata`, TX uplink modes).

For normal Scotland-wide traffic, many people use the `#scotland` channel with the `sco` scope. For local traffic, set **scope** to the code that matches the area, whatever channel name you use. For **`#ireland`**, use **`ioi` or `sco`** as described in [Scopes](scopes); `#norniron` is commonly used with `ioi`.

## Useful MeshCore background

- [Region Filtering](https://blog.meshcore.io/2026/01/20/region-filtering)
- [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope)
- [CLI Commands](https://docs.meshcore.io/cli_commands/)
