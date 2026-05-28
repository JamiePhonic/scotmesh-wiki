---
title: MeshCore FAQ
description: Frequently asked questions about ScotMesh and MeshCore.
published: true
date: 2026-05-18T23:56:00.000Z
tags: meshcore, scotland, faq, beginner
editor: markdown
dateCreated: 2026-05-18T23:56:00.000Z
---

# MeshCore FAQ 🙋

Quick answers to the questions that come up most often. If yours is not here, ask on [Discord](https://discord.gg/invite/VvagXJn7Bq).

---

## Do I need a radio licence to use ScotMesh?

No. MeshCore uses licence-exempt LoRa frequencies (868 MHz in the UK). Anyone can carry a companion node and use the app. No amateur radio licence required.

---

## What is the range?

It depends heavily on where you are and whether there is a repeater nearby. A companion node in the open might reach a couple of kilometres to a nearby repeater. A well-sited repeater on a hill can cover tens of kilometres. In a city with buildings in the way, range is shorter.

The [MeshCore Node Map](https://map.meshcore.io/) shows where ScotMesh repeaters are — check there to see if you have coverage near you.

---

## Why can't I hear anyone?

A few things to check, in order:

1. **Scope is wrong.** The most common cause. Go to **Experimental Settings** in the app and confirm **Default Scope Region** is set to `sco`. Then check the channel scope too — see [Scopes](/meshcore/scopes).
2. **No repeater nearby.** Check the [MeshCore Node Map](https://map.meshcore.io/) to see if there is a repeater in your area.
3. **Wrong radio preset.** Make sure your device is flashed with the **EU/UK (Narrow)** preset. A device on the wrong channel or spreading factor will not hear anything.
4. **Device not transmitting.** Try `#test` with scope `sco` — you should at least see your own message go out.

If you have checked all of the above and still hear nothing, ask on [Discord](https://discord.gg/invite/VvagXJn7Bq).

---

## What is the difference between a channel and a scope?

- A **channel** is a named group chat — `#scotland`, `#glasgow`, `#test`. It is just a label for people.
- A **scope** is a region code that repeaters use to decide whether to carry your message — `sco`, `gla`, `edi`.

You can send a message on `#glasgow` with the scope set to `sco` and it will go Scotland-wide. Or you can set the scope to `gla` and it will only travel through Glasgow-area repeaters. The channel name does not change that — the scope does. See [Scopes](/meshcore/scopes) for the full explanation.

---

## Why is the `*` wildcard not allowed?

The `*` wildcard tells repeaters to forward everything to everyone. On a well-grown network that floods the airtime with traffic that most people do not need. ScotMesh uses deliberate region scopes instead — set `sco` for Scotland-wide, `gla` for Glasgow, and so on — so traffic only travels where it is actually useful.

There is one exception: `*` is used as a root parent in repeater configuration commands (for example `region put sco *`). That is a region tree concept, not wildcard forwarding. See [Regions](/meshcore/regions) for the detail.

---

## Can I use ScotMesh without a repeater nearby?

Yes, but your range is very limited. Two companion nodes in line of sight can talk directly. If there is no repeater between you and another user, messages will only reach as far as direct radio range allows — often just a few hundred metres in built-up areas.

If you want to extend coverage in your area, the best thing to do is put up a repeater. See [Repeater Quick Setup](/meshcore/repeater-quick-setup).

---

## What device should I buy?

The [MeshCore Flasher](https://meshcore.io/flasher) lists devices that can be flashed with MeshCore firmware — that is a good starting point for what is currently supported. Popular choices include boards from Heltec, LilyGo, and RAK, but the community's preferences do shift as new hardware comes out.

The best thing to do is ask on [Discord](https://discord.gg/invite/VvagXJn7Bq) — someone will point you at whatever is working well right now.

---

## How do I know if my device is working?

Send a message on `#test` with scope `sco`. If you can see the message appear in the app after sending, the device is transmitting. If someone else on the network responds, you have confirmed two-way comms.

You can also check the [MeshCore Node Map](https://map.meshcore.io/) — if your node has an observer uplink configured, it should appear there.

---

## Do I need to set scope for every channel separately?

Not necessarily. If you set a **default scope** of `sco` in Experimental Settings, that applies to any channel that does not have its own scope override. You only need to set a per-channel scope when you want something different — for example `gla` on `#glasgow` to keep traffic local, or `ioi` on `#ireland` for the Island of Ireland path. See [Scopes](/meshcore/scopes) for the full detail.

---

## What is the Island of Ireland (`ioi`) scope?

ScotMesh and the Irish MeshCore community have a peering agreement. Repeaters on both sides carry the `ioi` scope so that traffic can move between the two networks in a controlled way — without flooding everything. You can join `#ireland` and set scope to `ioi` to talk on that path. See [Channels](/meshcore/channels) for more.

---

## Something else not answered here?

Jump on [Discord](https://discord.gg/invite/VvagXJn7Bq) — the community is friendly and happy to help.
