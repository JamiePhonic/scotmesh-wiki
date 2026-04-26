---
title: MeshCore Region Guide for Scotland
description: This guide explains how we propose to use regions in the Scottish MeshCore network, with view on future expansion beyond the Central region.
published: true
date: 2026-04-26T11:03:52.978Z
tags: meshcore, regions, scotland
editor: markdown
dateCreated: 2026-04-25T11:46:10.885Z
---

# MeshCore Region Guide for Scotland

> Status: Draft proposal for community review

This guide describes the proposed MeshCore region code structure for Scotland, with an initial focus on Central Scotland.

It is intended as a practical community guide for repeater owners, node operators, and anyone helping to plan the Scottish MeshCore network.

The aim is to keep region codes simple, readable, and useful as the Scottish MeshCore network grows.

## Purpose of this guide

This guide explains how we propose to use **regions** in the Scottish MeshCore network, with a particular focus on Central Scotland.

The aim is to give repeater owners, node operators, and new users a simple shared system for describing where traffic should travel.

A good region plan helps the mesh grow without becoming messy, overloaded, or confusing.

This document is written for ordinary users as well as repeater administrators. It explains the basic ideas in plain English first, then gives the agreed region codes and suggested configuration approach.

## What MeshCore is, in plain English

MeshCore is a radio messaging system that allows small LoRa devices to communicate directly with each other without relying on mobile phone masts, Wi-Fi, or the internet.

A typical MeshCore setup contains three broad types of device:

| Device type | Plain English explanation |
|---|---|
| **Companion node** | A small radio that connects to your phone, tablet, or computer. You use it to send and receive messages. |
| **Repeater** | A fixed radio, often placed high up, whose job is to hear MeshCore traffic and repeat it so it can travel further. |
| **Standalone node** | A device with its own screen or controls that can operate without needing a phone. |

In simple terms:

Your message leaves your node by radio.  
A nearby repeater hears it.  
That repeater passes it on.  
Other repeaters may pass it further.  
Eventually, the message reaches the intended person or area.

That is the power of a mesh network — but it also creates a problem.

If every repeater repeats everything everywhere, the network can become noisy and inefficient as it grows. That is where **regions** come in.

## Why regions are needed

When a mesh is small, it is fine for most traffic to be repeated widely. There are only a few nodes, a few repeaters, and not much congestion.

As the network grows, especially across Scotland, we need a more organised approach.

Regions help us:

1. **Keep local traffic local**  
   A message about Falkirk does not always need to be repeated across Dundee, Perth, Glasgow, Edinburgh, and beyond.

2. **Reduce unnecessary radio traffic**  
   LoRa is slow compared with Wi-Fi or mobile data. Every unnecessary repeat uses airtime.

3. **Improve reliability**  
   Less unnecessary repeating means more room for useful messages.

4. **Make the network easier to understand**  
   The analyzer, maps, and community planning become clearer when repeaters are tagged with recognisable areas.

5. **Support future growth**  
   A regional system lets Scotland grow into multiple linked areas without every decision needing to be remade later.

The simple version is:

> Regions help the network know where messages should go.

## Regions and scopes: the key idea

There are two related concepts: **regions** and **scopes**.

### Region

A **region** is a label configured on a repeater.

It tells the network:

> This repeater serves this area.

For example, a repeater in Central Scotland might be configured with:

- `sco`
- `cen`
- `fal`

That would mean:

- `sco` — Scotland
- `cen` — Central Scotland
- `fal` — Falkirk area

### Scope

A **scope** is a label applied to a message or channel.

It tells the network:

> This message is intended for this area.

For example, a message scoped to `fal` should only be repeated by repeaters that have been configured to serve `fal`.

This is not about stopping people from receiving normal public traffic. It is about giving the mesh a way to avoid sending every message everywhere when that is not needed.

## The wildcard region `*`

MeshCore also uses a wildcard region:

- `*`

This is important.

The wildcard means:

> Repeat messages that have no specific region scope.

In practical terms, it keeps the network working in the traditional way for normal, unscoped traffic.

Our rule is:

> **Leave `*` enabled unless there is a very specific technical reason not to.**

The `*` region is the exception to our three-letter code rule.

## Our agreed Scottish region code approach

For Scotland, we agreed to use **simple three-letter lowercase codes**.

We are deliberately keeping the visible region codes short and easy to remember.

We are **not** using long prefixed names such as:

- `gb-sco`
- `gb-cen`
- `sco-fal`

Instead, we use:

- `sco`
- `cen`
- `fal`

This makes the system easier to read in the app, on the analyzer, and in community discussions.

Important note: other countries and communities may use ISO-style hierarchical codes such as `gb-sco`, `nl-dr`, or `ch-de`. That is a valid approach, but our Scottish proposal is a local community convention designed for simplicity and readability.

## Agreed region codes

### Country level

- `sco` — Scotland

### Regional level

- `cen` — Central Scotland
- `tay` — Tayside
- `fif` — Fife

### City / local area level

- `gla` — Glasgow area
- `edi` — Edinburgh area
- `fal` — Falkirk area
- `dun` — Dundee area
- `per` — Perth area

## Recommended hierarchy

Although we are not putting the hierarchy into the code name itself, we can still think of the system as a hierarchy:

- `sco`
  - `cen`
    - `fal`
    - `edi`
    - `gla`
  - `fif`
  - `tay`
    - `dun`
    - `per`

In plain English:

- **National:** `sco` — Scotland-wide
- **Regional:** `cen` — Central Scotland
- **Local:** `fal` — Falkirk area

This gives us a clean structure without making the codes too long.

## Suggested repeater configuration policy

A repeater should normally be configured with:

1. The wildcard region `*`
2. The country code `sco`
3. The relevant regional code
4. The relevant local code, if appropriate
5. Any neighbouring region codes that the repeater genuinely serves

### Example: Falkirk / Central Scotland repeater

A repeater covering the Falkirk area would usually have:

- `*`
- `sco`
- `cen`
- `fal`

### Example: Edinburgh-facing Central Scotland repeater

A repeater that mainly serves Central Scotland but has strong coverage towards Edinburgh might use:

- `*`
- `sco`
- `cen`
- `edi`

### Example: high-site repeater bridging several areas

A high repeater with genuine coverage into multiple areas could use:

- `*`
- `sco`
- `cen`
- `fal`
- `edi`
- `gla`
- `fif`

This should be used carefully.

The point of regions is to keep traffic sensible. A repeater should not claim every possible region just because it can occasionally hear distant nodes.

## Good practice for repeater owners

Repeater owners should try to follow these principles.

### Use lowercase

Always use lowercase:

- `sco`
- `cen`
- `fal`

Avoid mixed case:

- `SCO`
- `Cen`
- `FAL`

Lowercase keeps the analyzer and community documentation consistent.

### Use agreed codes

Do not invent a new code if an agreed one already exists.

For example, use:

- `edi`

Not:

- `edn`
- `edinburgh`
- `gb-edi`

### Add only the areas your repeater genuinely serves

A repeater should be honest about its coverage.

If a repeater is in Falkirk and mainly serves Falkirk and Central Scotland, it should not automatically add Dundee, Perth, Glasgow, and Fife unless it genuinely provides useful coverage into those areas.

### Keep `*` enabled

The wildcard keeps ordinary unscoped traffic working.

Removing it could make your repeater behave unexpectedly for users who have not yet configured scopes.

### Coordinate before adding new codes

If a new area needs a code, agree it publicly before using it.

This avoids two groups using different codes for the same place.

## Suggested command examples

The exact method may vary depending on firmware version and whether you are using the app, web configurator, USB serial, or remote admin.

For our three-letter Scottish scheme, a Central Scotland / Falkirk repeater may look conceptually like this:

- `region put sco`
- `region put cen sco`
- `region put fal cen`
- `region allowf sco`
- `region allowf cen`
- `region allowf fal`
- `region save`

Then check the result with:

- `region`

For a Tayside / Dundee repeater:

- `region put sco`
- `region put tay sco`
- `region put dun tay`
- `region allowf sco`
- `region allowf tay`
- `region allowf dun`
- `region save`

For a Fife repeater:

- `region put sco`
- `region put fif sco`
- `region allowf sco`
- `region allowf fif`
- `region save`

The parent relationship is useful because it lets us keep short codes while still describing a logical structure.

Always check for an `OK` response where applicable, and remember to save the configuration so it survives a reboot.

## Firmware and app version notes

Region and scope support depends on MeshCore firmware and app support.

The safest recommendation is:

> Use the latest stable MeshCore firmware and app available for your device.

For region work, repeater owners should aim to keep their MeshCore firmware and client apps up to date.

Older firmware may still pass normal traffic, but region management may not behave as expected.

## What this means for ordinary users

Most ordinary users do not need to worry about region configuration immediately.

If you are using a companion node, your normal messages should still work through repeaters that keep the wildcard `*` enabled.

Regions become more relevant when:

**You run a repeater**  
You need to tell the mesh what area your repeater serves.

**You help plan the network**  
Regions make coverage and routing easier to understand.

**You want local-only traffic**  
Scopes can help keep messages within the intended area.

**You use analyzer tools**  
Region codes make repeaters easier to filter and identify.

For a casual user, the simple version is:

> Regions help the network know where messages should go.

## What this means for repeater owners

Repeater owners have more responsibility because repeaters shape the behaviour of the mesh.

A well-configured repeater helps the network.

A badly configured repeater can cause confusion, unnecessary traffic, or misleading analyzer data.

Before changing a repeater’s region list, ask:

1. Where is this repeater physically located?
2. What area does it reliably serve?
3. Is it a local repeater, a regional repeater, or a high-site bridge?
4. Does it need neighbouring regions?
5. Have the local community agreed the codes?

## Proposed Scottish starting standard

The following should be treated as the starting standard for the Scottish MeshCore community.

### Core national code

- `sco`

All Scottish repeaters should normally include `sco`.

### Central Scotland

- `cen`

Use for repeaters serving the wider Central Scotland belt.

### Local Central Scotland areas

- `fal` — Falkirk area
- `edi` — Edinburgh area
- `gla` — Glasgow area

### Nearby regions

- `fif` — Fife
- `tay` — Tayside

### Tayside local areas

- `dun` — Dundee area
- `per` — Perth area

## Example configurations

### Falkirk local repeater

Use when the repeater mainly serves Falkirk and surrounding Central Scotland.

- `*`
- `sco`
- `cen`
- `fal`

### Linlithgow / West Lothian style repeater

Depending on coverage, a repeater in this area may reasonably bridge Falkirk and Edinburgh-facing traffic.

- `*`
- `sco`
- `cen`
- `fal`
- `edi`

### Edinburgh area repeater

- `*`
- `sco`
- `cen`
- `edi`

### Glasgow area repeater

- `*`
- `sco`
- `cen`
- `gla`

### Fife repeater

- `*`
- `sco`
- `fif`

If it also provides useful Central Scotland coverage:

- `*`
- `sco`
- `fif`
- `cen`

### Dundee repeater

- `*`
- `sco`
- `tay`
- `dun`

### Perth repeater

- `*`
- `sco`
- `tay`
- `per`

## Naming and publishing new region codes

When a new Scottish area needs a code, the following rules should be used:

1. Use three letters.
2. Use lowercase.
3. Make it obvious to local users.
4. Avoid clashing with existing agreed codes.
5. Avoid overly small areas unless there is a real need.
6. Discuss it with the local MeshCore community before publishing it.

Examples of possible future codes might include:

- `stg` — Stirling
- `liv` — Livingston
- `abe` — Aberdeen
- `inv` — Inverness
- `ayr` — Ayrshire
- `bor` — Borders

These are examples only and should not be treated as agreed until the community confirms them.

## Common questions

### Do regions replace normal MeshCore messaging?

No.

Regions simply help control where scoped traffic is repeated.

Normal unscoped traffic can still be repeated through the wildcard `*`.

### Should every repeater have `sco`?

In Scotland, yes, that is the recommended baseline.

### Should every repeater have every Scottish region?

No.

That would defeat the purpose of regions.

Repeaters should only list the areas they genuinely serve.

### Should we use `gb-sco` instead of `sco`?

Not for this agreed Scottish scheme.

Some wider UK or international guides use ISO-style codes such as `gb-sco`. That is a valid approach, but our local agreement is to use short three-letter codes.

### Is `edi` an airport code or a MeshCore region code?

In this guide, `edi` means the Edinburgh area.

It happens to match the familiar airport-style code, but here it is being used as a local MeshCore region label.

### Can a repeater be in more than one region?

Yes.

That is useful for high sites, border areas, or repeaters that genuinely link neighbouring areas.

## Summary

Regions give the Scottish MeshCore community a simple way to organise the network as it grows.

Our agreed approach is:

- Use three-letter lowercase codes.
- Use `sco` for Scotland.
- Use `cen`, `tay`, and `fif` for major regions.
- Use `fal`, `edi`, `gla`, `dun`, and `per` for local areas.
- Keep `*` enabled for ordinary unscoped traffic.
- Do not use long prefixes such as `gb-sco` or `sco-fal` in this local scheme.

The initial agreed region list is:

- `sco` — Scotland
- `cen` — Central Scotland
- `tay` — Tayside
- `fif` — Fife
- `gla` — Glasgow
- `edi` — Edinburgh
- `fal` — Falkirk
- `dun` — Dundee
- `per` — Perth

This gives us a clean, readable, and expandable foundation for building a coordinated Scottish MeshCore network.




