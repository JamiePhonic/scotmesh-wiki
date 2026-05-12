---
title: MeshCore Scopes
description: Companion App guidance for choosing and setting MeshCore region scope in Scotland.
published: true
date: 2026-05-11T21:52:00.000Z
tags: meshcore, regions, scotland, meshcore_app
editor: markdown
dateCreated: 2026-04-28T19:59:20.685Z
---

# MeshCore Scopes

> **Scotland:** If you do not have a suitable **scope** set, repeaters on the Scottish MeshCore network may not forward your traffic. You can end up **shouting into the void**. Check your default scope and each channel’s scope before you count on messages reaching anyone.
{.is-warning}

This guide is for MeshCore Companion App users in Scotland. **Scope** is what repeaters use to decide whether to forward a message; the channel name is mainly for humans. In normal use, set your **default** scope to `sco`, then set **per-channel** scope when you need something narrower (or different).

> **ScotMesh setup:** Under **Experimental Settings**, set the default scope region to `sco`, and keep `ioi` available in your scope list as well so you can pick it when you need it. For each channel, set scope to match **where the traffic should travel**—for example `#fife` with `fif`. On **`#ireland`**, you may use **`ioi` or `sco`**: use `ioi` when the message should ride the Island of Ireland scoped path (IOI peering); use `sco` when you want the same channel but Scotland-wide scoped carriage on the mesh.
{.is-info}

## Why scope matters

The Scotland regional framework gives repeaters a structured way to carry the right traffic. Companion App users help that work by choosing scope deliberately.

- Keep Scottish traffic inside Scotland where appropriate.
- Allow controlled traffic to and from the Island of Ireland (IOI peering).
- Reduce unnecessary flooding.
- Avoid unscoped traffic.
- Keep the network easier to grow.

For example channel names and typical scopes, see [Channels](channels). For repeater region codes, see [Regions](regions).

## What region scope means

In MeshCore, a message can carry a **region scope**. That code tells repeaters which region the traffic is intended for.

```text
sco = Scotland-wide
fif = Fife (example local)
ioi = Island of Ireland (IOI peering)
```

A message scoped to `sco` is forwarded by repeaters that carry `sco`. A message scoped to `ioi` is forwarded by repeaters that carry `ioi`. If scope is missing or wrong for your path, the message may go nowhere useful.

## Wildcard forwarding is not allowed

The wildcard marker is:

```text
*
```

Do not rely on wildcard **forwarding** for routing. The Scottish MeshCore setup expects explicit region scopes for normal use.

```text
Do not set scope to * for forwarding
Use a real region code instead
```

In the **Companion App**, your channel scope should always be a **real region code** (`sco`, `fif`, `ioi`, and so on)—not `*` for forwarding. On **repeaters**, CLI examples sometimes show `*` as the **parent** in a region tree (for example `region put sco *`); that is a different idea from wildcard **forwarding** and is covered in [Regions](regions).

## Documented scope codes

| Scope | Typical use |
|---|---|
| `sco` | Scotland-wide traffic |
| `cen` | Central Scotland |
| `fif` | Fife |
| `tay` | Tayside |
| `gla` | Glasgow area |
| `edi` | Edinburgh area |
| `fal` | Falkirk area |
| `per` | Perth area |
| `dun` | Dundee area |
| `ioi` | Island of Ireland / IOI peering |
{.dense}

For most day-to-day traffic in Scotland, **`sco`** is the right default. Use a **local** code when traffic should stay in that area, regardless of channel name.

Do not use the old combined name:

```text
ioi-sco
```

## Default scope and per-channel scope

On ScotMesh, set your **default** scope region to:

```text
sco
```

In the mobile app this is usually under **Experimental Settings**. Flood packets from the companion then use `sco` unless a **group channel** has its own scope.

**Per-channel scope overrides the default.** Examples:

- `#fife` with `fif` keeps traffic in the Fife-shaped part of the mesh.
- **`#ireland` with `ioi`** — message is scoped for the Island of Ireland path (IOI peering repeaters).
- **`#ireland` with `sco`** — same channel name, but the packet is Scotland-wide scoped; repeaters treat it like other `sco` traffic. Use when that matches how you want the message to move (for example mainly Scottish-side repeaters, or you are experimenting).

Keep both `sco` and `ioi` in your available scopes so you can switch. For background, see MeshCore [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope).

## How to set region scope in the Companion App

Menus vary by app version and platform; the usual flow is:

```text
1. Open the MeshCore Companion App
2. Open the channel you want to use
3. Open the channel options or channel menu
4. Find the region scope option
5. Select or add the region code you need
6. Send with that scope active
```

Often the channel menu includes something like **Set Region Scope**, then you pick or type the code (for example `sco`, `fif`, or `ioi`).

More on region filtering: [Region Filtering](https://blog.meshcore.io/2026/01/20/region-filtering).

## Examples

**Scotland-wide**

```text
Channel: #scotland
Scope:   sco
```

**Local (example)**

```text
Channel: #fife
Scope:   fif
```

**`#ireland` with Island of Ireland scope**

```text
Channel: #ireland
Scope:   ioi
```

**`#ireland` with Scotland-wide scope**

```text
Channel: #ireland
Scope:   sco
```

The channel name does not set scope by itself—you still choose `ioi` or `sco` (or another code) in the channel settings.

## Channel name versus scope

Being in a channel called `#ireland` does **not** automatically set scope. You must set **`ioi` or `sco`** (or another deliberate code) for that channel so repeaters see the intent you want.

Wrong:

```text
Channel: #ireland
Scope:   none / blank / wildcard forwarding
```

## Quick choices

- Normal Scottish chat: default `sco`, or `#scotland` with `sco`.
- Local-only: local scope such as `fif` when traffic should stay local.
- **`#ireland`:** `ioi` for IOI-scoped path, **`sco`** when you want Scotland-wide scoped carriage on that channel.
- Tests: `#test` with whichever scope you are testing (`fif`, `sco`, …).

If you are unsure, **`sco`** is the safe general default for Scottish-side traffic.

## What to avoid

- Sending important traffic with no region scope.
- Relying on wildcard forwarding.
- Assuming the channel name alone chooses routing.
- Using `ioi-sco`.

## Summary

```text
Default: sco on ScotMesh
Override per channel when needed
#ireland: ioi OR sco — pick the path you mean
Local: use the local code when traffic should stay local
Never: scope * for forwarding, or ioi-sco
Check scope before you send
```

Getting scope right keeps the mesh predictable and easier to grow.
