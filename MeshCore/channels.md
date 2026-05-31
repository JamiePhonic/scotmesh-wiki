---
title: MeshCore Channels
description: Guidance for MeshCore channel names and region scopes in the Scottish MeshCore network.
published: true
date: 2026-05-31T18:34:34.164Z
tags: meshcore, scotland, channels
editor: markdown
dateCreated: 2026-05-28T13:04:06.889Z
---

# MeshCore Channels (now and in the future)

Channels are where the conversation happens. Think of them like group chats — anyone with the right device and scope set can join in. There is nothing stopping you creating your own, but the ones below are the agreed community channels so everyone knows where to find each other.

In the Scottish MeshCore network, what really matters for routing is **region scope** — not the channel name. The channel name is for people; the scope is for the mesh.

## 🏷️ Channel name and scope

A channel name and a region scope are related, but they are not the same thing.

For example:

```text
Channel: #edinburgh
Scope:   edi
```

The channel name is what you see. The scope is what tells the mesh to carry your message through Edinburgh-area repeaters.

> Joining a channel does not automatically set the scope.
>
> Before sending, check the channel settings in the Companion App and make sure the scope matches where you want the message to travel.
{.is-info}

## 📡 Current (2026)  and proposed (2027 and beyond) channels

The following table lists known community channels and proposed channels for Scotland.

**Type is documentation only; it is not a Companion App setting**. It groups channels by how you pick them: **Wide** for large-footprint traffic (whether the scope is `sco` or `ioi`), **Regional** for Scottish region area channels, and **Local** for Scottish City / town / metropolitan areas. Set **Scope** to match the reach you want.

| Channel | Type | Scope | Status | Use |
|---|---|---|---|---|
| `#scotland` | Wide | `sco` | Current | General Scotland-wide MeshCore traffic. |
| `#ireland` | Wide | `ioi` or `sco` | Current | General Island of Ireland traffic. |
| `#norniron` | Wide | `ioi` or `sco` | Current | Northern Ireland Traffic |
| `#central` | Regional | `cen` | Proposed | Central Scotland traffic. |
| `#dundee` | Local | `dun` | Proposed | Dundee area traffic. |
| `#edinburgh` | Local | `edi` | Proposed | Edinburgh area traffic. |
| `#falkirk` | Local | `fal` | Proposed | Falkirk area traffic. |
| `#fife` | Regional | `fif` | Current | Fife area traffic. |
| `#glasgow` | Local | `gla` | Proposed | Glasgow area traffic. |
| `#perth` | Local | `per` | Proposed | Perth area traffic. |
| `#tayside` | Regional | `tay` | Proposed | Tayside traffic. |
| `#test` | Wide | Set the scope being tested | Current | Test messages. Use `sco`, `edi`, `gla`, or another scope that matches what you are testing. ||
{.dense}

> As of Summer 2026, The ScotMesh MC Mesh is still in its early growth phase. As such there is no pressing requirement to restrict in-country traffic to sub regions or local regions.   In practical terms country wide traffic will not cause us any issues for at least another year, probably longer. So the country wide region `sco` will be enough until then.

Proposed channels are shared names the community is still settling on. They are listed here so that people can talk about the same idea using the same name and scope, rather than ending up with several competing versions.

## 🤔 Choosing the right channel in the future (2027 and beyond

Use the **narrowest scope** that still fits what you are sending. Examples:

```text
#scotland / sco          Scotland-wide mesh (Current)
#edinburgh / edi         Local area (same idea for #glasgow/gla, #fife/fif, #dundee/dun, …)(Future)
#test / <scope>          Pick the scope you are actually testing (current)
#ireland / ioi or sco    Island of Ireland channel (pick scope for the path you want) (current)
```

## 👍 Good practice for the future expanded mesh

- Keep local traffic local where possible.
- Use `#test` for test messages so normal channels stay readable.
- Use Scotland-wide scope only when the conversation is relevant across Scotland.
- Use `ioi` when the message belongs on the Island of Ireland scope, or `sco` on `#ireland` when you want Scotland-wide scoped carriage (see [Scopes](/meshcore/scopes)).
- Wildcard forwarding will remain disable in the Scottish setup.
- New public channel names tend to land better when discussed with the community first.
- Always check the Companion App scope before sending — a wrong scope and your message goes nowhere useful.

For more detail on setting scope in the Companion App, see [Scopes](/meshcore/scopes). For repeater and region code guidance, see [Regions](/meshcore/regions). For **MQTT observers** and map uplink, see [Observers](/meshcore/observers).
