---
title: MeshCore Channels
description: Guidance for MeshCore channel names and region scopes in the Scottish MeshCore network.
published: true
date: 2026-05-11T21:52:00.000Z
tags: meshcore, channels, scotland
editor: markdown
dateCreated: 2026-05-11T21:52:00.000Z
---

# MeshCore Channels

Channels give MeshCore users a shared place to talk about a topic or area. A clear channel list helps people find the right conversation without flooding the whole network with traffic that only matters to one place or group.

In the Scottish MeshCore network, you can use or create any channel name that suits your group. What matters for routing is **region scope**: set it so it matches where the traffic should travel. The channel name is for people; the scope is for the mesh.

## Channel name and scope

A channel name and a region scope are related, but they are not the same thing.

For example:

```text
Channel: #fife
Scope:   fif
```

The channel name is what users see. The scope is what helps the mesh carry the message through the right repeaters.

> Joining a channel does not always mean the correct scope has been set.
>
> Before sending, check the channel settings in the Companion App and that the scope matches where you want the message to travel (or the test you are carrying out).
{.is-info}

## Current and proposed channels

The following table lists known community channels and proposed channels for Scotland. The local channels follow the documented Scottish region scopes.

**Type** is documentation only; it is not a separate Companion App setting. It groups channels by how you pick them: **Wide** for large-footprint traffic (whether the scope is `sco` or `ioi`), **Local** for Scottish geographic area channels, and **Other** for topic coordination and testing. Set **Scope** to match the reach you want (or the test you are running).

| Channel | Type | Scope | Status | Use |
|---|---|---|---|---|
| `#scotland` | Wide | `sco` | Current | General Scotland-wide MeshCore traffic. |
| `#ireland` | Wide | `ioi` or `sco` | Current | General Island of Ireland traffic. Use `ioi` for the IOI-scoped path or `sco` when you want Scotland-wide scoped carriage on this channel—see [Scopes](scopes). |
| `#norniron` | Wide | `ioi` | Current | Northern Ireland Traffic |
| `#central` | Local | `cen` | Proposed | Central Scotland traffic. |
| `#dundee` | Local | `dun` | Proposed | Dundee area traffic. |
| `#edinburgh` | Local | `edi` | Proposed | Edinburgh area traffic. |
| `#falkirk` | Local | `fal` | Proposed | Falkirk area traffic. |
| `#fife` | Local | `fif` | Current | Fife area traffic. |
| `#glasgow` | Local | `gla` | Proposed | Glasgow area traffic. |
| `#perth` | Local | `per` | Proposed | Perth area traffic. |
| `#tayside` | Local | `tay` | Proposed | Tayside traffic. |
| `#test` | Other | Set the scope being tested | Current | Test messages. Use `sco`, `fif`, `edi`, or another scope that matches what you are testing. |
| `#scotham` | Other | `sco` | Proposed | Scotland-wide amateur radio, UHF, and related coordination. |
{.dense}

Proposed channels are shared names the community is still settling on. They are listed here so that people can talk about the same idea using the same name and scope, rather than ending up with several competing versions.

## Choosing the right channel

Use the **narrowest scope** that still fits what you are sending; channel names are up to you. Set **Scope** to match the reach you want (or the area you are testing on `#test`). Examples:

```text
#scotland / sco          Scotland-wide mesh (example name)
#fife / fif              Local area (same scope idea for #edinburgh/edi, #glasgow/gla, …)
#test / <scope>          Pick the scope you are actually testing
#ireland / ioi or sco    Island of Ireland channel (pick scope for the path you want)
#norniron / ioi         Northern Ireland (example)
```

## Good practice

- Keep local traffic local where possible.
- Use `#test` for test messages so normal channels stay readable.
- Use Scotland-wide scope only when the conversation is relevant across Scotland.
- Use `ioi` when the message belongs on the Island of Ireland scope, or `sco` on `#ireland` when you want Scotland-wide scoped carriage (see [Scopes](scopes)); channel name is flexible.
- Wildcard forwarding is not part of the usual Scottish setup.
- New public channel names tend to land better when discussed with the community first.
- Checking the Companion App scope before sending helps avoid misrouted messages.

For more detail on setting scope in the Companion App, see [Scopes](scopes). For repeater and region code guidance, see [Regions](regions).
