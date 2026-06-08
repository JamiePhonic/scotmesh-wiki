---
title: MeshMapper-Friendly Repeater Configuration Spec for Scotmesh MeshCore
description: 
published: true
date: 2026-06-08T08:31:09.128Z
tags: 
editor: markdown
dateCreated: 2026-06-08T08:31:09.128Z
---

# MeshMapper-Friendly Repeater Configuration Spec for Scotmesh MeshCore

These are guidelines for a uniform configuration of repeaters taking part in **Scotmesh MeshCore**.

These are not hard and fast rules, but certain specifications are necessary for smooth MeshMapper reporting. Using these settings will help ensure a smooth-running mesh.

---

## Identification

Use **ASCII characters only** for the repeater name.

This makes MeshMapper management much easier, as most emoji characters are **not** read by MeshMapper.

You can use a single emoji to customise your MeshCore app icon on your companion radio, but this has no effect on the repeater name as seen by MeshMapper.

---

## Location

Repeater location should be set as accurately as possible, while still protecting the safety and security of the repeater site.

For example, setting the repeater location around **200 metres** from the real location gives a search area of approximately **12.6 hectares**. This would take a careful walking search of around **8 hours** to cover.

Setting the location **200–250 metres away** from the real position gives a useful level of obfuscation while still allowing the repeater to appear correctly on MeshMapper.

If no location is set:

- The repeater will be excluded from MeshMapper
- You will not see useful telemetry, such as zero-hop neighbours
- Routing path analysis, enhancements and other mesh planning will not be possible

---

## Basic Owner Information

Please ensure basic owner information is set.

---

## Advert Settings

Recommended settings:

- **Zero-hop advert:** 60–120 minutes
- **Flood advert:** 24 hours

---

## Radio Settings

Please use:

- **EU/UK Narrow**
- **Frequency:** 869.618 MHz
- **Spreading Factor:** SF8
- **Coding Rate:** CR8
- **Bandwidth:** 62.5 kHz

Recommended CLI settings:

```text
set multi.acks 1
set path.hash.mode 2
```

This enables:

- **Multi ACKs**
- **3-byte path hash**

Please keep your repeater updated with the latest firmware whenever possible.

Please also ensure your companion radio or radios are set to:

- **Double ACKs on**
- **3-byte path hash**

---

## Access

Do not leave the guest login with no password.

For continuity, please set the guest password to:

```text
hello
```

This gives at least some security over the guest login.

Keep your admin password safe.

---

## Region / Scope

Please set both the **default scope** and **home scope** to:

```text
sco
```

Please also deny flood to:

```text
*
```

Channels set to region `sco` are:

- `Public`
- `#scotland`

Optionally, you may also add the channel:

```text
#ireland
```

with region:

```text
ioi
```

Scotland and the Island of Ireland have collaborated very well to construct a civilised MeshCore environment.

As Scotmesh expands, we may add nested sub-regions within `sco`.

---

## Time Setting and Synchronisation with MeshMapper

After power-up of the repeater, the time is always incorrect.

Please use the following procedure to set the correct time and synchronise it with MeshMapper.

This process assumes you have already configured the repeater for use.

### Phone App Method

1. Open the settings page in the phone app.
2. Perform the usual **Sync Clock** action.
3. Scroll to the bottom of the page.
4. Tap **Reboot**.

Unlike pressing the physical **reset** button on the repeater board, this is a **soft reset**.

A soft reset does **not** reset the clock, but it appears to be important for finalising certain settings.

For reference:

- Pressing **Reboot** in the app is a **soft reset**
- Pressing the physical reset button on the board is a **hard reset**
- A hard reset resets all settings not stored in flash

You may also use CLI commands to perform the same task if preferred.

---

## Closing Note

I hope this helps with the ease of configuration.

This guide assumes you already understand the menu and command structure of MeshCore repeaters, devices and apps.

If there is a menu item you cannot find, ask on the Discord server and one of the admins or knowledgeable users will help you along.ur content here