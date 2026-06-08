---
title: MeshCore Regions
description: Scotland region code and repeater guidance for the Scottish MeshCore network.
published: true
date: 2026-06-08T08:06:43.592Z
tags: meshcore, scotland, regions
editor: markdown
dateCreated: 2026-05-28T13:04:23.987Z
---

# MeshCore Regions

---

> ### NOTE - A Regional Framework was impelemented in the ScotMesh Meshcore Mesh at the beginning of April 2026. This was out of sheer necessity as our mesh was dying under the flood traffic from England (24,000 flood packets & 600+ messages daily). This saved our mesh from descending into a chaotic, unusable mess of incoherent rambles and frustrated messaging failures. This is why an understaning of regions is imperative to understanding where we are today 


---


This guide is for **repeater owners**. 

The aim is simple: keep the scheme readable, predictable, and usable as the network grows.

## Why regions are needed

MeshCore messages travel through repeaters for onward routing. Whilst this is the core function, if every repeater carries every message everywhere, the network becomes noisy, inefficient and flooded with uneccessary traffic.

Regions help us:

1. **Keep local traffic local**  
   In the future, a message that only matters in one area wont always need to be repeated across every part of Scotland.

2. **Reduce unnecessary radio traffic**  
   LoRa is subject to a finite airtime cycle per hour (compared with Wi-Fi or mobile data), so every avoidable repeat uses valuable airtime.

3. **Improve reliability**  
   Less unnecessary repeating leaves more room for useful messages.

4. **Make planning clearer**  
   Regions make repeater deployment easier to map, identify needs, plan future expansion  and ease of ongoing mesh maintenance.

5. **Support controlled peering**  
   Strategic repeaters can deliberately carry neighbouring traffic, such as the **IOI peering agreement** between Scotland and the Island of Ireland.

## Regions and scopes

There are two related concepts: **regions** and **scopes**.

| Term | Meaning | Example |
|---|---|---|
| **Region** | A  label configured on a repeater to describe the area it serves. | An Edinburgh-area repeater includes `edi`. |
| **Scope** | A  label applied to messages or channels to describe which area (or region) the traffic is intended to travel. | The `#glasgow` channel might use `gla` when traffic should stay in that area. |
{.dense}

In a densely populated mesh, a repeater should only carry scoped traffic for regions it genuinely serves.  In new or embryonic meshes, this requirment will be a future need but best practise planning mandates introducing regions as early as is practical.

## Wildcard forwarding is not allowed (see info box at top of this document for context).

The wildcard marker is:

```text
*
```

> The important rule is: `*` will appear as a root parent in the region tree, but wildcard forwarding must be denied.
>
> In other words, `region put sco *` is  correct, but must be preceeded by `region denyf *` .
{.is-warning}

The Scottish MeshCore setup does not allow wildcard forwarding. Repeater owners must deny wildcard forwarding with:

```text
region denyf *
```

You may still see `*` as the root parent when defining the region tree, for example `region put sco *`. That is different from allowing wildcard forwarding.

For channel names and suggested scopes, see [Channels](https://wiki.scotmesh.uk/en/MeshCore/channels). 

## Scottish region code approach

For Scotland, we use simple three-letter lowercase codes.

We are not part of any UK wide mesh (for context see comment box at the top of this documnet) Therefore, **we are not using any long prefixed names**


We use short codes such as:

```text
sco
cen
fal
```

Other countries and communities may use ISO-style hierarchical codes. That is  valid for them, but the Scottish convention is designed to be short and easy to read in apps, analyser tools, and community discussions.


## Current (June 2026) Agreed region codes

| Code | Area |
|---|---|
| `sco` | Scotland |
| `cen` | Central Scotland |
| `fif` | Fife |
| `tay` | Tayside |
| `gla` | Glasgow area |
| `edi` | Edinburgh area |
| `fal` | Falkirk area |
| `dun` | Dundee area |
| `per` | Perth area |
| `ioi` | Island of Ireland (`ioi`) — IOI peering |
{.dense}

## IOI peering agreement

The Scottish and Irish MeshCore communities maintain a **peering agreement**: scoped traffic is carried on the other network only where **both** sides configure for it.

Under that agreement, Scottish repeaters add the `ioi` region alongside `sco` where the Scottish baseline applies, and Island of Ireland repeaters add `sco` alongside their own region codes in the same spirit. Messages with matching **scopes** can then move between the two networks predictably, without relying on wildcard forwarding. For example channel names and typical scopes, see [Channels](https://wiki.scotmesh.uk/en/MeshCore/channels).

The `ioi` code is  **not** a Scottish local region. It marks repeaters and traffic that deliberately participate in that peering.

Do not use:

```text
ioi-sco
```

Use:

```text
ioi
```

### Peering with Scotland (other regions)

If another region wants to peer with Scotland in a similar way, they should already have the following in place:

1. **Wildcard flooding disallowed** on their repeaters (the same principle as the Scottish setup: deny wildcard forwarding with `region denyf *`; see [Wildcard forwarding is not allowed](#wildcard-forwarding-is-not-allowed)).
2. **Appropriate regions on their repeaters** so traffic is not forwarded wider than intended, and Scottish repeaters are not flooded with scoped traffic they did not agree to carry.
3. **Neighbouring Scotland in RF terms** so equipment can **directly** peer, rather than assuming long unofficial relay chains.

When that fits your situation, contact the Scottish Mesh community on [Discord](https://discord.gg/invite/VvagXJn7Bq) so we can discuss scope names, boundaries, and a safe rollout.

## Recommended hierarchy

Although the hierarchy is not written into the code itself, it can be thought of like this:

```text
sco
  cen
    fal
    edi
    gla
  fif
  tay
    dun
    per
ioi
```

In plain English:

- `sco` is for Scotland-wide traffic.
- `tay`, `cen`, and `fif` are Scottish sub regions.
- `fal`, `edi`, `gla`, `dun`, and `per` are local areas.
- `ioi` is for the Island of Ireland under the IOI peering agreement.

## Suggested repeater configuration policy

A Scottish repeater should normally be configured with:

1. The country code `sco`.
2. The `ioi` code for IOI peering.
3. The relevant regional code.
4. The relevant local code, if appropriate.
5. Any neighbouring codes that the repeater genuinely serves.

> Do not allow wildcard forwarding.
>
> In command line interface (CLI) examples, this means using `region denyf *`
{.is-warning}

### Falkirk / Central Scotland repeater

A repeater covering the Falkirk area would usually have:

```text
sco
ioi
cen
fal
```

### Edinburgh-facing Central Scotland repeater

A repeater that mainly serves Central Scotland but has strong coverage towards Edinburgh might use:

```text
sco
ioi
cen
edi
```

### Fife repeater

A Fife repeater would usually have:

```text
sco
ioi
fif
```

If it genuinely provides useful Central Scotland coverage, it may also include:

```text
cen
```

### Scottish repeaters and `ioi`

Scottish repeaters should normally include `ioi` alongside `sco` as part of the [IOI peering agreement](#ioi-peering-agreement):

```text
sco
ioi
```

That keeps peering-capable forwarding available where the Scottish baseline is configured. It does not make `ioi` a Scottish local region.

## Good practice for repeater owners

Use lowercase region codes. Do not use mixed case such as `SCO`, `Cen`, or `FAL`.

Use agreed codes. For example, use `edi` for the Edinburgh area, not `edn`, `edinburgh`, or `gb-edi`.

Add only the areas your repeater genuinely serves. A high-site repeater may reasonably serve several areas, but a repeater should not claim every region just because it can occasionally hear distant nodes.

Coordinate before adding new codes. If a new area needs a code, discuss it publicly before using it so that the community does not end up with competing names for the same place.

## Suggested command examples

The exact method may vary depending on firmware version and whether you are using the app, web configurator, USB serial, or remote administration. The upstream reference is the MeshCore [CLI Commands](https://docs.meshcore.io/cli_commands/) documentation, especially the region management commands.

> New to repeater setup?
>
> Start with [Repeater Quick Setup](https://wiki.scotmesh.uk/en/MeshCore/repeater-quick-setup), then come back here for the fuller detail.
{.is-info}

For a Central Scotland / Falkirk repeater, the setup may look conceptually like this:

```text
region put sco *
region put ioi *
region put cen sco
region put fal cen

region allowf sco
region allowf ioi
region allowf cen
region allowf fal

region denyf *

region default sco

region save
```

Then check the result with:

```text
region
```

For a Tayside / Dundee repeater:

```text
region put sco *
region put ioi *
region put tay sco
region put dun tay

region allowf sco
region allowf ioi
region allowf tay
region allowf dun

region denyf *

region default sco

region save
```

For a Glasgow-area repeater:

```text
region put sco *
region put ioi *
region put gla sco

region allowf sco
region allowf ioi
region allowf gla

region denyf *

region default sco

region save
```

For a repeater that serves Scotland, Central Scotland, Glasgow, Edinburgh, and IOI peering (`ioi`):

```text
region put sco *
region put cen sco
region put gla cen
region put edi cen
region put ioi *

region allowf sco
region allowf cen
region allowf gla
region allowf edi
region allowf ioi

region denyf *

region default sco

region save
```

On firmware that supports default scope, repeater and room server administrators should also set the default scope for packets that originate from that node:

```text
region default sco
```

> **Set `region default sco` on your repeater.**
>
> Without a default scope, adverts sent by your repeater go out unscoped. Because the Scottish network uses `region denyf *`, other repeaters will reject those unscoped adverts and will never learn your repeater exists. Setting the default scope to `sco` ensures your adverts are carried normally across the mesh.
{.is-warning}

This is separate from flood forwarding permissions. For more detail, see [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope).

Always check for an `OK` response where applicable, and remember to save the configuration so it survives a reboot.

## Firmware and app version notes

Region and scope support depends on MeshCore firmware and app support.

Use the latest stable MeshCore firmware and app available for your device. Older firmware may still pass some traffic, but region management and scope handling may not behave as expected.

MeshCore region filtering was introduced across firmware and app releases, and default scope support was added later. The MeshCore posts [Region Filtering](https://blog.meshcore.io/2026/01/20/region-filtering) and [Default Scope Region](https://blog.meshcore.io/2026/04/17/default-scope) are useful background when checking version behaviour.

## Naming and publishing new region codes

When a new Scottish area needs a code, use these rules:

1. Use three lowercase letters.
2. Make the code obvious to local users.
3. Avoid clashing with existing agreed codes.
4. Avoid overly small areas unless there is a real need.
5. Discuss the code with the local MeshCore community before publishing it.

Examples of possible future codes might include:

```text
sti = Stirling
liv = Livingston
abe = Aberdeen
inv = Inverness
ayr = Ayrshire
bor = Borders
```

These are examples only and should not be treated as agreed until the community confirms them.

## Common questions

### Do regions replace normal MeshCore messaging?

No. Regions help control where scoped traffic is repeated.

### Should every Scottish repeater have `sco` and `ioi`?

Yes, that is the recommended baseline for Scottish repeaters. Use `sco` for Scotland and add `ioi` alongside it for the IOI peering agreement.

### Should every repeater have every Scottish region?

No. That would defeat the purpose of regions. Repeaters should only list the areas they genuinely serve.

### Should we use `gb-sco` instead of `sco`?

Not for this Scottish scheme. Some wider UK or international guides use ISO-style codes, but the local Scottish agreement is to use short three-letter codes.

### Can a repeater be in more than one region?

Yes. That is useful for high sites, border areas, or repeaters that genuinely link neighbouring areas.

### Can we allow `*` for compatibility?

No. The Scottish MeshCore setup does not allow wildcard forwarding. Use the correct region scope instead.

## Summary

Regions give the Scottish MeshCore community a simple way to organise the network as it grows.

Our agreed approach is:

- Use three-letter lowercase codes.
- Use `sco` for Scotland.
- Add `ioi` wherever the Scottish baseline `sco` is configured (IOI peering).
- Use `cen`, `tay`, `gla`, and `fif` for major regions where they match coverage.
- Use `fal`, `edi`, `gla`, `dun`, and `per` for local areas.
- Use `ioi` for Island of Ireland traffic under the IOI peering agreement.
- Deny wildcard forwarding with `region denyf *`.
- Do not use long prefixes such as `gb-sco` or `sco-fal` in this local scheme.

This gives us a clean, readable, and expandable foundation for building a coordinated Scottish MeshCore network.