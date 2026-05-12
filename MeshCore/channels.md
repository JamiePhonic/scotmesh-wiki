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

In the Scottish MeshCore network, a channel should normally have an agreed **region scope**. The channel name is for people. The scope is for the mesh.

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
> Before sending, check the channel settings in the Companion App and make sure the scope matches the channel or the test you are carrying out.
{.is-info}

## Current and proposed channels

The following table lists known community channels and proposed channels for Scotland. The local channels follow the documented Scottish region scopes.

| Channel | Scope | Status | Use |
|---|---|---|---|
| `#scotland` | `sco` | Current | General Scotland-wide MeshCore traffic. |
| `#test` | Set the scope being tested | Current | Test messages. Use `sco`, `fif`, `edi`, or another agreed scope depending on what you are testing. |
| `#central` | `cen` | Proposed | Central Scotland traffic. |
| `#fife` | `fif` | Current | Fife area traffic. |
| `#glenrothes` | `fif` | Proposed | Glenrothes area traffic, scoped through Fife. |
| `#tayside` | `tay` | Proposed | Tayside traffic. |
| `#glasgow` | `gla` | Proposed | Glasgow area traffic. |
| `#edinburgh` | `edi` | Proposed | Edinburgh area traffic. |
| `#falkirk` | `fal` | Proposed | Falkirk area traffic. |
| `#dundee` | `dun` | Proposed | Dundee area traffic. |
| `#perth` | `per` | Proposed | Perth area traffic. |
| `#ireland` | `ioi` | Current | Traffic for the Ireland / Island of Ireland interconnect. |
| `#scotham` | `sco` | Proposed | Scotland-wide amateur radio, UHF, and related coordination. |
{.dense}

Proposed channels are not rules yet. They are listed here so that people can talk about the same idea using the same name and scope, rather than ending up with several competing versions.

## Choosing the right channel

Use the most specific channel that matches the purpose of the message.

For general Scottish traffic, use:

```text
Channel: #scotland
Scope:   sco
```

For local traffic, use the agreed local channel and scope where one exists:

```text
Channel: #fife
Scope:   fif
```

Other local examples include:

```text
Channel: #edinburgh
Scope:   edi

Channel: #glasgow
Scope:   gla

Channel: #falkirk
Scope:   fal
```

For test messages, use `#test` and set the scope to the area you are actually testing:

```text
Channel: #test
Scope:   sco
Use:     Scotland-wide test

Channel: #test
Scope:   fif
Use:     Fife test

Channel: #test
Scope:   edi
Use:     Edinburgh area test
```

For the Ireland interconnect, use:

```text
Channel: #ireland
Scope:   ioi
```

For amateur radio, UHF, and related organising across Scotland, the proposed channel is:

```text
Channel: #scotham
Scope:   sco
```

## Good practice

- Keep local traffic local where possible.
- Use `#test` for test messages so normal channels stay readable.
- Use Scotland-wide scope only when the conversation is relevant across Scotland.
- Use `ioi` only for the Ireland / Island of Ireland interconnect.
- Do not rely on wildcard forwarding; it is not allowed in the Scottish setup.
- Do not create new public channel names without discussing them with the community.
- Make sure the Companion App is using the correct scope before sending.

For more detail on setting scope in the Companion App, see [Scopes](scopes). For repeater and region code guidance, see [Regions](regions).
