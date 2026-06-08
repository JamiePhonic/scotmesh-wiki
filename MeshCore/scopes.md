---
title: MeshCore Scopes
description: Companion App guidance for choosing and setting MeshCore region scope in Scotland.
published: true
date: 2026-06-08T08:16:42.568Z
tags: meshcore_app, meshcore, scotland, regions
editor: markdown
dateCreated: 2026-05-28T13:04:32.228Z
---

# MeshCore Scopes

> **Quick start for most users:** open the app, go to **Experimental Settings**, set **Default Scope Region** to `sco`. That is all you need for normal Scottish traffic.
{.is-success}

> **Watch out:** if you do not have a suitable **scope** set, repeaters on the Scottish MeshCore network wont forward your traffic. You can end up **shouting into the void**. Check your default scope and each channel's scope before you count on messages reaching anyone.
{.is-warning}

Scope is the single setting that makes or breaks whether your messages go anywhere on ScotMesh. The channel name is for people — the scope is for the mesh. Set your **default** to `sco`, then adjust per channel when you need something narrower.

> **ScotMesh setup:** Under **Experimental Settings**, set the default scope region to `sco`, and keep `ioi` available in your scope list as well so you can pick it when you need it. For each channel, set scope to match **where the traffic should travel**—for example `#edinburgh` with `edi`. On **`#ireland`**, you may use **`ioi` or `sco`**: use `ioi` when the message should ride the Island of Ireland scoped path (IOI peering); use `sco` when you want the same channel but Scotland-wide scoped carriage on the mesh.
{.is-info}

## 🤷 Why scope matters

Without scope, repeaters have no way to know whether to carry your traffic. With it, messages travel through exactly the right part of the network.

- Keep Scottish traffic inside Scotland where appropriate.
- Allow controlled traffic to and from the Island of Ireland (IOI peering).
- Reduce unnecessary flooding.
- Keep the network easier to grow.

For example channel names and typical scopes, see [https://wiki.scotmesh.uk/en/MeshCore/channels](/meshcore/channels). For repeater region codes, see [https://wiki.scotmesh.uk/en/MeshCore/regions.

## 🗺️ What region scope means

Think of scope like a postcode on a letter — it tells the mesh where the message is meant to go.

```text
sco = Scotland-wide
edi = Edinburgh area (example local)
ioi = Island of Ireland (IOI peering)
```

A message scoped to `sco` is forwarded by repeaters that carry `sco`as a region. A message scoped to `ioi` is forwarded by repeaters that carry `ioi`as a region. If scope is missing or wrong for your path, the message will go nowhere, it is dropped and ceases to exist.

## 🚫 Wildcard forwarding is not allowed

The wildcard marker is `*`. Do not rely on it for routing — the Scottish MeshCore setup expects explicit region scopes.

In the **Companion App**, your channel scope should always be a **real region code** (`sco`, `gla`, `ioi`, and so on). On **repeaters**, CLI examples sometimes show `*` as the **parent** in a region tree (for example `region put sco *`); that is a different idea from wildcard **forwarding** and is covered in https://wiki.scotmesh.uk/en/MeshCore/regions.

## 📋 Documented scope codes

| Scope | Typical use |
|---|---|
| `sco` | Scotland-wide traffic |
| `cen` | Central Scotland |
| `fif` | Fife |
| `tay` | Tayside |
| `gla` | Glasgow area |
| `edi` | Edinburgh area |
| `fal` | Falkirk area |
| `sti` | Stirling area |
| `per` | Perth area |
| `dun` | Dundee area |
| `ioi` | Island of Ireland / IOI peering |
{.dense}

For most day-to-day traffic in Scotland, **`sco`** is the right default. Use a **local** code when traffic should stay in that area, regardless of channel name.


## ⚙️ Default scope and per-channel scope

On ScotMesh, set your **default** scope region to `sco`. In the mobile app this is usually under **Experimental Settings**. Flood packets from the companion then use `sco` unless a **group channel** has its own scope.

**Per-channel scope overrides the default.** Examples:

- `#glasgow` with `gla` keeps traffic in the Glasgow-area part of the mesh.
- **`#ireland` with `ioi`** — message is scoped for the Island of Ireland path (IOI peering repeaters).
- **`#ireland` with `sco`** — same channel name, but the packet is Scotland-wide scoped; repeaters treat it like other `sco` traffic.

Keep both `sco` and `ioi` in your available scopes so you can switch. For background, see MeshCore [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope).

## 📱 How to set region scope in the Companion App

Menus vary by app version and platform; the usual flow is:

```text
1. Open the MeshCore Companion App
2. Open the channel you want to use
3. Open the channel options or channel menu
4. Find the region scope option
5. Select or add the region code you need
6. Send with that scope active
```

Often the channel menu includes something like **Set Region Scope**, then you pick or type the code (for example `sco`, `edi`, or `ioi`).


## 💬 Examples

**Scotland-wide**

```text
Channel: #scotland
Scope:   sco
```

**Local (example)**

```text
Channel: #glasgow
Scope:   gla
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

The channel name does not set scope by itself — you still choose `ioi` or `sco` (or another code) in the channel settings.

## ⚡ Quick choices

- Normal Scottish chat: default `sco`, or `#scotland` with `sco`.
- Local-only: local scope such as `edi` or `gla` when traffic should stay in that area.
- **`#ireland`:** `ioi` for IOI-scoped path, **`sco`** when you want Scotland-wide scoped carriage on that channel.
- Tests: `#test` with whichever scope you are testing (`tay`, `sco`, …).

If you are unsure, **`sco`** is the safe general default for Scottish-side traffic.

## ❌ What to avoid

- Sending traffic with no region scope.
- Relying on wildcard forwarding.
- Assuming the channel name alone chooses routing.

## 📝 Summary

```text
Default: sco on ScotMesh
Override per channel when needed
#ireland: ioi OR sco
Local: use the local code when traffic should stay local
Check your companion app is scoped before you send your initial messages
```

Getting scope right keeps mesh traffic logical and the mesh relaible, easier to use and simpler to grow.
