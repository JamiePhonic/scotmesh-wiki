---
title: MeshCore Repeater Quick Setup
description: A short ScotMesh guide for setting up a MeshCore repeater with the right region settings.
published: true
date: 2026-05-12T09:54:00.000Z
tags: meshcore, repeater, scotland
editor: markdown
dateCreated: 2026-05-12T09:54:00.000Z
---

# MeshCore Repeater Quick Setup

This is the short version for setting up a MeshCore repeater on ScotMesh.

A repeater helps the network by hearing MeshCore traffic and passing it on. A good repeater in a good location can make a big difference for everyone nearby.

> ScotMesh does not use wildcard forwarding.
>
> Add the right regions, allow those regions, and deny wildcard forwarding with `region denyf *`.
{.is-warning}

## Quick settings

| Setting | Use |
|---|---|
| Configurator | MeshCore web flasher: `https://meshcore.io/flasher` |
| Preset | EU/UK (Narrow) |
| Device role | Repeater |
| Browser | Chrome or Edge |
| Baseline regions | `sco`, `ioi` |
| Local regions | Add only the areas the repeater genuinely serves |
| Wildcard forwarding | Deny with `region denyf *` |
| Flood advert interval | 24 hours |
| Default scope | `sco` — **required** so other repeaters accept your adverts |
{.dense}

## Before you start

You will need:

- A supported LoRa device — open the [MeshCore Flasher](https://meshcore.io/flasher) to see what can be flashed, or ask on [Discord](https://discord.gg/invite/VvagXJn7Bq).
- A USB data cable, not a charge-only cable.
- A laptop or desktop with Chrome or Edge.
- A sensible repeater location.
- Reliable power.

> Location matters more than almost anything else.
>
> A modest repeater in a high, clear spot is usually more useful than a powerful setup hidden indoors.
{.is-info}

## Choose your region settings

Start with `sco` and `ioi`, then add the local areas the repeater genuinely covers.

| Location / coverage | Regions to add | Notes |
|---|---|---|
| Any Scottish repeater | `sco`, `ioi` | Baseline ScotMesh setup. |
| Fife | `sco`, `ioi`, `fif` | Fife-wide coverage. |
| Central Scotland | `sco`, `ioi`, `cen` | Wider Central belt coverage. |
| Falkirk | `sco`, `ioi`, `cen`, `fal` | Falkirk local coverage. |
| Edinburgh area | `sco`, `ioi`, `cen`, `edi` | Edinburgh-facing Central Scotland coverage. |
| Glasgow area | `sco`, `ioi`, `cen`, `gla` | Glasgow-facing Central Scotland coverage. |
| Tayside | `sco`, `ioi`, `tay` | Wider Tayside coverage. |
| Dundee area | `sco`, `ioi`, `tay`, `dun` | Dundee local coverage. |
| Perth area | `sco`, `ioi`, `tay`, `per` | Perth local coverage. |
| High site / bridge | `sco`, `ioi`, plus genuinely served areas | Do not add every region just because it is listed. |
{.dense}

## Simple setup flow

1. Open the MeshCore web flasher in Chrome or Edge.
2. Select your device.
3. Choose the repeater role.
4. Use the EU/UK (Narrow) preset.
5. Flash the device.
6. Set a clear repeater name.
7. Add the right regions from the table above.
8. Set flood adverts to 24 hours.
9. Deny wildcard forwarding.
10. Set `region default sco`.
11. Save the region configuration.

## Simple command examples

### Baseline Scottish repeater

Use this when the repeater is part of ScotMesh but does not have a more specific local region yet.

```text
region put sco *
region put ioi *

region allowf sco
region allowf ioi

region denyf *

set flood.advert.interval 24

region default sco

region save
```

> Without `region default sco`, your repeater's adverts are sent unscoped. The Scottish network denies unscoped forwarding (`region denyf *`), so other repeaters will reject those adverts and will not know your repeater is there.
{.is-warning}

### Fife repeater

Use this when the repeater serves Fife.

```text
region put sco *
region put ioi *
region put fif sco

region allowf sco
region allowf ioi
region allowf fif

region denyf *

set flood.advert.interval 24

region default sco

region save
```

### Central Scotland / Falkirk repeater

Use this when the repeater serves Falkirk and wider Central Scotland.

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

set flood.advert.interval 24

region default sco

region save
```

## Good repeater habits

- Put the repeater as high and clear as you reasonably can.
- Use stable power.
- Keep the antenna vertical.
- Give the repeater a name people can recognise.
- Add only the regions it genuinely serves.
- Use `region denyf *`; do not allow wildcard forwarding.
- Set `region default sco` so your adverts are accepted by the rest of the mesh.
- Set flood adverts to 24 hours.
- Ask the community before inventing new region codes.

## Where to go next

- [Regions](/meshcore/regions) has the fuller region guide and more command examples.
- [Scopes](/meshcore/scopes) explains what Companion App users need to set.
- [Channels](/meshcore/channels) lists the agreed and proposed channels.
- [MeshCore CLI Commands](https://docs.meshcore.io/cli_commands/) is the upstream command reference.

## Appendix: what the key commands mean

| Command | Meaning |
|---|---|
| `region put sco *` | Create `sco` at the top of the region tree. |
| `region put fif sco` | Create `fif` as a child of `sco`. |
| `region allowf sco` | Allow scoped flood traffic for `sco`. |
| `region denyf *` | Deny unscoped wildcard forwarding. |
| `set flood.advert.interval 24` | Set flood adverts to 24 hours. |
| `region default sco` | Set the default scope so adverts from this repeater are scoped to `sco` and accepted by the mesh. |
| `region save` | Save the region configuration. |
{.dense}
