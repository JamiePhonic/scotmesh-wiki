---
title: Regions and the Companion app
description: Wiki describing the changes in the companion app
published: true
date: 2026-04-28T19:59:20.685Z
tags: meshcore, regions, scotland, meshcore_app
editor: markdown
dateCreated: 2026-04-28T19:59:20.685Z
---

# MeshCore Scotland Region Scoping  
## Companion App Region & Message Scope Setup

This guide explains how MeshCore Companion App users in Scotland should configure and use **region scope** correctly.

The Scotland regional framework gives us a structured way to manage repeater traffic. This second guide explains what ordinary Companion App users need to do so that their messages are sent with the correct scope.

The aim is simple:

- keep Scottish traffic inside Scotland where appropriate
- allow controlled traffic to neighbouring regions such as Ireland
- reduce unnecessary flooding
- avoid relying on the wildcard `*`
- make the network more scalable as MeshCore use grows

This guide should be read alongside the main Scotland regional framework.

## 1. What “region scope” means

In MeshCore, a message can be given a **region scope**.

The scope tells repeaters which region that message is intended for.

For example:

```text
sco  = Scotland
ioi  = Island of Ireland / Ireland neighbouring region
cen  = Central Scotland
fif  = Fife
tay  = Tayside
gla  = Glasgow
edi  = Edinburgh
fal  = Falkirk
per  = Perth
dun  = Dundee
```

If a message is scoped to `sco`, it should be carried by repeaters that support the `sco` region.

If a message is scoped to `ioi`, it should be carried by repeaters that support the `ioi` region.

If no scope is set, the message may rely on repeaters still allowing wildcard or unscoped traffic. That is what we are trying to move away from.

## 2. Why Scotland is moving away from wildcard traffic

Historically, many repeaters have allowed the wildcard region:

```text
*
```

The wildcard is useful during early testing because it allows broad flooding of traffic.

However, as the network grows, wildcard traffic becomes inefficient. It can cause messages to travel much further than needed, using airtime on repeaters that do not need to carry that traffic.

The long-term aim is that Scottish users should not depend on wildcard flooding for normal use.

Instead, messages should be scoped properly.

In simple terms:

```text
Do not rely on *
Use the correct region scope instead
```
## 3. What Companion App users need to do

Companion App users need to learn how to set the correct region scope when sending messages.

There are two main things to understand:

1. **Normal Scottish messages should usually use Scotland scope**
2. **Messages intended for a neighbouring region should use that neighbouring region’s scope**

For most users in Scotland, normal day-to-day traffic should use:

```text
sco
```

For traffic intended to go to Ireland / Island of Ireland, use:

```text
ioi
```
## 4. Recommended Scotland Companion App scopes

The following are the currently recommended region codes for Scotland (more will follow in the future):

```text
sco  = Scotland
cen  = Central Scotland
fif  = Fife
tay  = Tayside
gla  = Glasgow
edi  = Edinburgh
fal  = Falkirk
per  = Perth
dun  = Dundee
ioi  = Island of Ireland / Ireland neighbouring region
```

For general Scottish mesh traffic, use:

```text
sco
```

For a local area or city channel, use the relevant local code where that channel has been agreed locally.

For Ireland-facing traffic, use:

```text
ioi
```

Important: the neighbouring Ireland region is now referred to as:

```text
ioi
```

Do not use the older combined name:

```text
ioi-sco
```
## 5. How to set a region scope in the Companion App

The exact menu wording may vary slightly depending on app version and platform, but the general process is:

```text
1. Open the MeshCore Companion App

2. Open the channel you want to use

3. Open the channel options / channel menu

4. Look for the region scope option

5. Select or add the required region code

6. Send your message with that region scope active
```

Some app versions allow region scope to be set from inside the channel screen.

In many cases this is done by opening the channel menu and selecting:

```text
Set Region Scope
```

Then choose or add the region you want to use.

Example:

```text
Set Region Scope → sco
```

Once the channel is scoped, messages sent in that channel should use that region.

## 6. Example: normal Scotland message

If you are in Scotland and want to send a normal public or regional message within Scotland, set the scope to:

```text
sco
```

Example use:

```text
Channel: Public / Scotland / agreed community channel
Scope:   sco
Message: Morning all, testing from Falkirk area.
```

This tells the network that the message is intended for Scotland.
## 7. Example: sending to Ireland / Island of Ireland

If you are in Scotland but want to send a message into the Ireland / Island of Ireland region, use:

```text
ioi
```

Example use:

```text
Channel: #ireland
Scope:   ioi
Message: Test from Scotland into ioi region.
```

This is important.

Do not leave the message unscoped and hope that wildcard repeaters will carry it.

The correct behaviour is:

```text
Use #ireland with region scope ioi
```
## 8. Channel scope versus message destination

It is important to understand that the channel name alone is not enough.

For example, being inside a channel called:

```text
#ireland
```

does not automatically guarantee that the message is scoped correctly.

The message still needs the correct region scope.

For Ireland traffic, that scope should be:

```text
ioi
```

So the correct setup is:

```text
Channel: #ireland
Scope:   ioi
```

Not simply:

```text
Channel: #ireland
Scope:   none / blank / wildcard
```
## 9. What scope should I use day to day?

For most users in Scotland:

```text
Use sco for normal Scottish traffic
```

Use local region codes only where there is a clear reason to keep the traffic more local (as of May'26 the Scottish Mesh is small so local only traffic is likley not needed yet).

Examples:

```text
sco  = general Scotland-wide traffic
cen  = Central Scotland traffic
fif  = Fife traffic
tay  = Tayside traffic
gla  = Glasgow traffic
edi  = Edinburgh traffic
fal  = Falkirk traffic
per  = Perth traffic
dun  = Dundee traffic
ioi  = Ireland / Island of Ireland traffic
```

If you are unsure, use:

```text
sco
```
## 10. Why this matters

Correct scoping helps the whole network.

It reduces unnecessary flooding, improves reliability, and makes it easier for repeaters to carry the traffic they are intended to carry.

Without proper scoping, messages may travel through areas that do not need them, creating avoidable load on the mesh.

With proper scoping, we can keep Scotland connected while still allowing controlled links to neighbouring regions.
## 11. What repeater owners should already be doing

Repeater owners should configure their repeaters with the agreed regional codes.

For Scotland, repeaters will normally include:

```text
sco
```

They may also include one or more local area codes, such as:

```text
cen
fif
tay
gla
edi
fal
per
dun
```

Border or strategic repeaters may also include the neighbouring region:

```text
ioi
```

The wildcard should eventually be removed from repeaters once the network is ready.

```text
*
```

The goal is not to break connectivity.

The goal is to move away from uncontrolled wildcard flooding and towards deliberate region-based routing.
## 12. What Companion App users should avoid

Please avoid sending important traffic with no region scope.

Please avoid relying on:

```text
*
```

Please avoid assuming that a channel name alone controls where the message goes.

Please avoid using old or incorrect region names.

In particular, do not use:

```text
ioi-sco
```

Use:

```text
ioi
```
## 13. Practical examples

### General Scottish test

```text
Channel: Public / Scotland channel
Scope:   sco
Message: Test from Linlithgow into Scotland region.
```

### Central Scotland message

```text
Channel: Central Scotland
Scope:   cen
Message: Test from Central Scotland.
```

### Falkirk local message

```text
Channel: Falkirk
Scope:   fal
Message: Local Falkirk test.
```

### Ireland / Island of Ireland message

```text
Channel: #ireland
Scope:   ioi
Message: Test from Scotland into ioi.
```
## 14. Suggested community standard

For Scotland, the suggested standard is:

```text
Normal Scotland-wide use:  sco
Local use:                 agreed local code
Ireland-facing use:         ioi
Wildcard use:               avoid / phase out
```

This keeps the setup simple for users while still allowing the network to grow in a controlled way.
## 15. Rollout advice

During the transition period, some repeaters may still allow wildcard traffic (not all owners have been traced).

That is expected.

However, users should start using proper region scope now so that, when wildcard is removed, messages continue to work.

The correct habit is:

```text
Open channel
Set the correct region scope
Send message
```

Not:

```text
Open channel
Send unscoped message
Hope wildcard carries it
```
## 16. Final summary

Scotland’s MeshCore network is moving towards proper regional scoping.

For Companion App users, the key points are:

```text
Use sco for normal Scottish traffic
Use ioi for Ireland / Island of Ireland traffic
Use local codes only where appropriate
Do not rely on *
Do not use ioi-sco
Make sure the channel has the correct region scope before sending
```

Getting this right now will help Scotland build a cleaner, more reliable, and more scalable MeshCore network.
