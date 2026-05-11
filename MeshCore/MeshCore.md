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
> If you use the MeshCore Companion App on our network, set your default region to `sco` under **Experimental Settings** and make sure `ioi` is also available for the Ireland interconnect. MeshCore calls this setting the **default scope region**. It helps ensure your messages are scoped for Scotland instead of relying on wildcard forwarding.
>
> For more background, see the MeshCore blog post [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope).
{.is-warning}

## Key ideas

MeshCore uses a few terms that are worth understanding before changing settings.

| Term | Meaning |
|---|---|
| **Channel** | A named place for conversation, such as `#scotland`, `#fife`, or `#ireland`. |
| **Scope** | The region code applied to messages in a channel, such as `sco`, `fif`, or `ioi`. |
| **Region** | A code configured on a repeater to describe the area it serves. |
| **Repeater** | A fixed node that hears MeshCore traffic and repeats it to extend coverage. |

A channel name alone does not control where traffic travels. The important routing detail is the **scope**. For example, the `#fife` channel should use the `fif` scope, while the `#ireland` interconnect should use the `ioi` scope.

## Scottish MeshCore guidance

The Scottish MeshCore network uses deliberate region-based routing. Messages should be sent with an agreed scope, and wildcard forwarding is not allowed in the Scottish setup.

## Start here

- [Channels](channels) explains the agreed and proposed MeshCore channels.
- [Regions](regions) explains the Scottish region code scheme and repeater guidance.
- [Scopes](scopes) explains how Companion App users should choose and set region scope.

For normal Scotland-wide traffic, use the `#scotland` channel with the `sco` scope. For local channels, use the agreed local scope. For the Ireland interconnect, use `#ireland` with the `ioi` scope.

## Useful MeshCore background

- [Region Filtering](https://blog.meshcore.io/2026/01/20/region-filtering)
- [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope)
- [CLI Commands](https://docs.meshcore.io/cli_commands/)