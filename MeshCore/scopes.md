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

This guide explains how MeshCore Companion App users in Scotland should choose and set **region scope**.

The short version is: set your default scope to `sco`, then use a more specific channel scope when you need one.

> If you are using the ScotMesh MeshCore network, set your Companion App default scope region to `sco` under **Experimental Settings** and make sure `ioi` is also available for the Ireland interconnect.
>
> Channel-specific scope still matters. A channel such as `#fife` should use `fif`, and `#ireland` should use `ioi`.
{.is-warning}

The Scotland regional framework gives repeaters a structured way to carry the right traffic. Companion App users help that system work by sending messages with the correct scope.

The aim is simple:

- Keep Scottish traffic inside Scotland where appropriate.
- Allow controlled traffic to neighbouring regions such as Ireland / Island of Ireland.
- Reduce unnecessary flooding.
- Avoid unscoped traffic.
- Make the network more scalable as MeshCore use grows.

For the channel list, see [Channels](channels). For repeater region guidance, see [Regions](regions).

## What region scope means

In MeshCore, a message can be given a **region scope**. The scope tells repeaters which region that message is intended for.

For example:

```text
sco = Scotland
fif = Fife
ioi = Ireland / Island of Ireland interconnect
```

If a message is scoped to `sco`, it should be carried by repeaters that support the `sco` region. If a message is scoped to `ioi`, it should be carried by repeaters that support the `ioi` interconnect.

If no scope is set, the message is not following the Scottish MeshCore guidance and may not travel as expected.

## Wildcard forwarding is not allowed

The wildcard marker is:

```text
*
```

Do not rely on it for message routing. The Scottish MeshCore setup does not allow wildcard forwarding for normal use.

In simple terms:

```text
Do not set scope to *
Use the correct region scope instead
```

## Recommended scopes

The currently documented scopes are:

| Scope | Use |
|---|---|
| `sco` | General Scotland-wide traffic |
| `cen` | Central Scotland traffic |
| `fif` | Fife traffic |
| `tay` | Tayside traffic |
| `gla` | Glasgow area traffic |
| `edi` | Edinburgh area traffic |
| `fal` | Falkirk area traffic |
| `per` | Perth area traffic |
| `dun` | Dundee area traffic |
| `ioi` | Ireland / Island of Ireland interconnect traffic |
{.dense}

For most users in Scotland, normal day-to-day traffic should use:

```text
sco
```

Also add or keep `ioi` available so that the `#ireland` channel can be scoped correctly when you need the interconnect.

For local area channels, use the relevant local code where that channel has been agreed locally.

For Ireland-facing traffic, use:

```text
ioi
```

Do not use the older combined name:

```text
ioi-sco
```

## Default scope region

Companion App users on the ScotMesh MeshCore network should set their default scope region to:

```text
sco
```

In the mobile app this is usually found under **Experimental Settings** as the default scope region name. When set, flood packets sent by the companion are scoped to that region unless a group channel has its own scope set.

Group channel scope still matters. If a channel has a specific scope, that channel scope should override the default. For example, `#fife` should use `fif`, while the general fallback for Scottish use should be `sco`. Keep `ioi` available wherever you add `sco`, so `#ireland` can use the `ioi` scope when needed.

For the upstream explanation, see [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope).

## How to set a region scope in the Companion App

The exact menu wording may vary depending on app version and platform, but the general process is:

```text
1. Open the MeshCore Companion App
2. Open the channel you want to use
3. Open the channel options or channel menu
4. Look for the region scope option
5. Select or add the required region code
6. Send your message with that region scope active
```

Some app versions allow region scope to be set from inside the channel screen. In many cases this is done by opening the channel menu and selecting:

```text
Set Region Scope
```

Then choose or add the region you want to use.

Example:

```text
Set Region Scope -> sco
```

Once the channel is scoped, messages sent in that channel should use that region.

MeshCore's region filtering background is explained in [Region Filtering](https://blog.meshcore.io/2026/01/20/region-filtering).

## Example: normal Scotland message

If you are in Scotland and want to send a normal public or regional message within Scotland, use:

```text
Channel: #scotland
Scope:   sco
Message: Morning all, testing from Falkirk area.
```

This tells the network that the message is intended for Scotland.

## Example: Fife message

If you are sending traffic intended for Fife, use:

```text
Channel: #fife
Scope:   fif
Message: Test from Fife.
```

## Example: sending to Ireland / Island of Ireland

If you are in Scotland but want to send a message into the Ireland / Island of Ireland region, use:

```text
Channel: #ireland
Scope:   ioi
Message: Test from Scotland into ioi region.
```

This is important. Do not leave the message unscoped and hope that other repeaters will carry it.

The correct behaviour is:

```text
Use #ireland with region scope ioi
```

## Channel name versus message scope

The channel name alone is not enough.

For example, being inside a channel called:

```text
#ireland
```

does not automatically guarantee that the message is scoped correctly. The message still needs the correct region scope:

```text
Channel: #ireland
Scope:   ioi
```

Not:

```text
Channel: #ireland
Scope:   none / blank / wildcard
```

## What scope should I use day to day?

For most users in Scotland:

```text
Use sco for normal Scottish traffic
```

Use local region codes only where there is a clear reason to keep the traffic more local. As of May 2026, the Scottish MeshCore network is still small, so local-only traffic may not be needed often.

For testing, use `#test` with the scope you are testing. For example, use `#test` with `fif` for a Fife test, or `#test` with `sco` for a Scotland-wide test.

If you are unsure, use:

```text
sco
```

## What to avoid

Please avoid:

- Sending important traffic with no region scope.
- Relying on wildcard forwarding.
- Assuming that a channel name alone controls where the message goes.
- Using old or incorrect region names such as `ioi-sco`.

## Final summary

For Companion App users, the key points are:

```text
Use sco for normal Scottish traffic
Use ioi for Ireland / Island of Ireland traffic
Use local codes only where appropriate
Do not set scope to *
Do not use ioi-sco
Make sure the channel has the correct region scope before sending
```

Getting this right now will help Scotland build a cleaner, more reliable, and more scalable MeshCore network.
