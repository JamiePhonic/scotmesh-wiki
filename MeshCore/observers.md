---
title: MeshCore Observers
description: How to set up an MQTT observer on a MeshCore repeater for ScotMesh, including MayoMesh, firmware, and uplink settings.
published: true
date: 2026-05-12T12:00:00.000Z
tags: meshcore, observers, mqtt, repeater, scotland
editor: markdown
dateCreated: 2026-05-12T12:00:00.000Z
---

# MeshCore Observers

An **MQTT observer** build is a repeater-style MeshCore firmware image that can **uplink** mesh traffic to one or more **MQTT** brokers. That feeds live maps and tools without replacing your normal RF repeater role, unless you deliberately turn repeating off for a receive-only site.

For how the bridge works (up to six broker slots, presets, `custom`, JWT `audience`, merged first flash, and more), see the upstream write-up: [MQTT_IMPLEMENTATION.md (agessaman fork)](https://github.com/agessaman/MeshCore/blob/mqtt-bridge-implementation-flex/MQTT_IMPLEMENTATION.md).

## Firmware

Prebuilt **repeater observer MQTT** binaries are published here:

[https://static.loraproject.ie/mqtt/](https://static.loraproject.ie/mqtt/)

Pick the file that matches your **exact board** (Heltec, LilyGo, RAK, Station G2, and others appear in the directory listing).

**`*_merged.bin` vs the non-merged `.bin`**

- **Files ending in `_merged.bin`** are a **full** image (bootloader, partition table, and application). Flashing one **normally wipes** stored repeater settings (**NVS**, Non-Volatile Storage: flash-backed preferences on ESP32-class boards, including Wi‑Fi, MQTT slots, name, keys, and similar). Use merged when you **need** that full layout refresh—for example the **first** move to observer firmware on a board, or when the observer build’s **partition table** is new for that hardware (see “Partition Table Changes” in [MQTT_IMPLEMENTATION.md](https://github.com/agessaman/MeshCore/blob/mqtt-bridge-implementation-flex/MQTT_IMPLEMENTATION.md)).
- **Files without `_merged` in the name** update the **app** only when the **partition layout is unchanged**. That path is what you want when you **already run observer firmware** on that board and you want to **keep** your current configuration through an upgrade.

After a merged flash, **re-enter** RF settings, node name, Wi‑Fi, MQTT, `mqtt.iata`, and other stored values. After a non-merged upgrade on the same layout, settings are **usually** kept—still read release notes. Later updates can use **OTA** ([`start ota`](#updates-without-usb-start-ota)) or a non-merged binary when appropriate.

## Updates without USB: `start ota`

On the repeater **serial console** (same place you run `set` / `get` commands), you can start the **over-the-air** path that brings up Wi‑Fi for firmware upload, so you do not have to plug in USB for every update. The exact command is:

```text
start ota
```

Use your build’s normal OTA workflow (browser or tool) once the device is advertising the update Wi‑Fi. Keep power stable during the flash.

## Observer setup

1. **Flash** the `*repeater_observer_mqtt*` file for your board ([Firmware](#firmware) explains **`_merged.bin`** vs non-merged).
2. **If NVS was wiped** (typical after **`_merged.bin`**; **NVS** is *Non-Volatile Storage*—flash-backed settings such as Wi‑Fi, MQTT, and radio prefs), set **RF and node identity** first: frequency, bandwidth, SF, CR, TX power, and **name** must match your mesh before the node is useful on air. Use the **device web UI** or admin screens, or serial, using your coordinator’s values; repeater planning is in [Regions](regions). **Then** work through **Wi‑Fi** → **`mqtt.iata`** → (optional **receive-only**) → **MQTT** in order below. **If you used a non-merged** update and kept settings, use `get` and only redo what is wrong—but **still check MQTT**: stock images often leave **LetsMesh Analyzer US** on **slot 1** and **LetsMesh Analyzer EU** on **slot 2** until you repoint them (for example MayoMesh on slot 1).

### Wi‑Fi

The observer needs LAN or internet path to the broker.

```text
set wifi.ssid YourWiFiNetwork
set wifi.pwd YourWiFiPassword
```

### Site code (`mqtt.iata`)

A short tag for **where the repeater sits**. It appears in MQTT topics and on maps—pick something stable (IATA-style codes are common).

| Code | Area |
|---|---|
| `EDI` | Edinburgh |
| `DND` | Dundee |
| `GLA` | Glasgow |

```text
set mqtt.iata EDI
```

### Optional: receive-only on RF

If this unit should **not** relay mesh traffic on air:

```text
set repeat off
```

### MQTT (MayoMesh on slot 1)

ScotMesh uses **MayoMesh** for the shared observer map and broker (who runs it and links: [MayoMesh live map](#mayomesh-live-map)). Observer builds usually ship with **LetsMesh Analyzer US** on **slot 1** and **LetsMesh Analyzer EU** on **slot 2**. Point **slot 1** at MayoMesh for our map. **Apply this whenever `get mqtt1.preset` is not already your MayoMesh custom setup**—including after a merged flash **and** after a non-merged upgrade from stock observer images.

```text
set mqtt1.preset custom
set mqtt1.server mqtt.mayomesh.net
set mqtt1.port 443
set mqtt1.audience mqtt.mayomesh.net
```

If you **only** use MayoMesh and want to free a second TLS slot on low-RAM boards (see upstream notes on PSRAM / two WSS connections):

```text
set mqtt2.preset none
```

Then:

```text
reboot
```

With **`audience`** set, the device uses **JWT (Ed25519)** sign-in to the broker, same idea as the built-in WSS presets in [MQTT_IMPLEMENTATION.md](https://github.com/agessaman/MeshCore/blob/mqtt-bridge-implementation-flex/MQTT_IMPLEMENTATION.md).

### Check

```text
get mqtt.status
get mqtt1.preset
get mqtt.tx
get mqtt.rx
```

Confirm the node shows on [meshcore.mayomesh.net](https://meshcore.mayomesh.net/) after a short wait.

## MayoMesh live map

- **Who runs it:** MayoMesh (the map and `mqtt.mayomesh.net` broker) is operated by **County Mayo**, **Ireland**. ScotMesh uses that community’s infrastructure for the shared observer map.
- **Live map:** [https://meshcore.mayomesh.net/](https://meshcore.mayomesh.net/) (MQTT over WebSocket, for example `wss://mqtt.mayomesh.net`, as shown on the site).
- **Broker commands** for your repeater are in [Observer setup](#observer-setup) under **MQTT (MayoMesh on slot 1)**.
- **Self-hosting the map UI:** based on [yellowcooln/meshcore-mqtt-live-map](https://github.com/yellowcooln/meshcore-mqtt-live-map); point your instance at MayoMesh’s broker instead of default LetsMesh-style endpoints.

## MQTT uplink: `mqtt.tx` advert vs `on`

These control **which of this node’s transmitted packets** are sent upstream over MQTT. **`mqtt.rx`** is separate (received packets).

| Setting | Effect |
|---|---|
| `set mqtt.tx advert` | Uplink **only this node’s own advert** TX packets. Lighter load; usually enough for map presence. |
| `set mqtt.tx on` | Uplink **all TX** from this node. Richer feed, more bandwidth and airtime. |
| `set mqtt.tx off` | No TX uplink over MQTT. |

For most map feeds, **`advert`** is enough:

```text
set mqtt.tx advert
```

If you need every TX packet this node sends mirrored upstream:

```text
set mqtt.tx on
```

Use **`on`** only when you intend that heavier feed (more bandwidth and airtime).

## Safety

Do not paste **Wi‑Fi passwords**, MQTT **passwords**, or private keys into public chats or screenshots. If **`mqtt.tx on`**, be mindful of **airtime** and how much traffic you export.

## See also

- [Regions](regions) — repeater region codes on the Scottish mesh.
- [MeshCore](meshcore) — hub page for channels, scopes, and related guides.
