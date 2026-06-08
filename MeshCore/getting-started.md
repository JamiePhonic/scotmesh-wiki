---
title: Getting Started with ScotMesh
description: A friendly beginner guide for new ScotMesh MeshCore users — from unboxing to sending your first message.
published: true
date: 2026-06-08T07:50:07.130Z
tags: meshcore, scotland, beginner, getting-started
editor: markdown
dateCreated: 2026-05-28T13:04:14.267Z
---

# Getting Started within ScotMesh 🏴󠁧󠁢󠁳󠁣󠁴󠁿


---


## 🏴󠁧󠁢󠁳󠁣󠁴󠁿 What is ScotMesh?

ScotMesh is community radio messaging networks across Scotland. It uses small, low-power LoRa radios to carry short messages between people — no mobile network, no Wi-Fi, no internet required. 
Think of it like a local text messaging service that works off-grid, powered by volunteer-run repeaters dotted across the country.


**Currently both Meshtastic and Mescore networks are available**

# **NOTE  This document focuses on Meschore**





Never used MeshCore before? Good — this is the place to start. No radio knowledge needed.

> This guide is written for **companion node** devices — small LoRa radios that pair with the MeshCore Companion App on your phone. More capable standalone devices do exist, but those are out of scope for this guide. If you are setting one of those up, ask in the [Discord](https://discord.gg/invite/VvagXJn7Bq) for advice.
{.is-info}




## 🎒 What you need

- A MeshCore **companion node** — a small LoRa radio that pairs with your phone over Bluetooth.
- A smartphone — Android or iPhone both work.
- That is it.

> Not sure which companion node to get? Ask in the [Discord](https://discord.gg/invite/VvagXJn7Bq) and the community can point you in the right direction.
{.is-info}

## 📱 1. Get the app

Download the **MeshCore Companion App** on your phone.

- **Android:** [MeshCore on Google Play](https://play.google.com/store/search?q=meshcore)
- **iPhone:** [MeshCore on the App Store](https://apps.apple.com/search?term=meshcore)

Open the app once it has installed.


## 👨‍💻 2. Flash the Latest Firmware to the LoRa Device

Before configuring the node, flash the LoRa device with the latest correct firmware for your exact hardware.

> **Important:** Do **not** use the firmware that came pre-installed on the node.

Pre-installed firmware may be outdated, built for a different board variant, or configured incorrectly for our mesh. Using the wrong firmware can cause connection issues, missing features, failed regional settings, or unreliable repeater behaviour.

Download the latest firmware from https://meshcore.io/, making sure you select the correct build for your exact device type, for example:

- RAK4631
- Heltec
- T114
- SenseCAP
- Waveshare
- Other supported hardware

After flashing, reboot the device and confirm the firmware version before continuing with the rest of the setup.



## 🔵 3. Connect your device

1. Make sure your LoRa device is powered on.
2. In the app, tap **Add Device** or the connect button.
3. The app will search for nearby devices over Bluetooth. Select yours from the list.
4. Wait a moment for it to connect. You should see your device appear in the app.

> If the device does not show up, make sure Bluetooth is enabled on your phone and that the device is in pairing mode. Check your device's instructions if you are unsure.
{.is-info}

## ⚙️ 3. The companion node settings


> For these settings, understanding the regional framework is important because it defines how traffic is organised and routed across the mesh. Regions (set on repeater nodes) allow the wider mesh to be split into sensible geographic areas, helping messages, adverts, and repeater traffic stay relevant to the area they are intended for while still allowing agreed neighbouring regions to interconnect where required. Setting the **default scope** tells the node which region it should use automatically when sending or repeating traffic that does not already have a specific scope applied. In practice, this helps keep local traffic local, reduces unnecessary flooding across unrelated areas, and improves the reliability and manageability of the mesh.


Before you can send anything from your companion app, you need to set it up for use in the ScotMesh MC mesh.


## Connecting a Newly Flashed Companion Node to ScotMesh

After flashing the latest companion-node firmware, use the **MeshCore app** to connect to the node by Bluetooth and configure it for ScotMesh.

1. Power on the newly flashed companion node.

2. Open the **MeshCore app** on your phone.

3. Make sure Bluetooth is enabled on your phone.

4. In the MeshCore app, go to the Bluetooth connection screen.

5. Scan for nearby Bluetooth MeshCore devices.

6. Select your newly flashed companion node from the list.

7. Wait for the app to connect to the node.

8. Confirm the node shows as connected in the MeshCore app.

9. Check the firmware version shown in the app and confirm it is the latest correct firmware for your device.

10. Give the node a clear and recognisable name so other ScotMesh users can identify it.

11. Open the node settings in the MeshCore app.

12. Set the LoRa/radio region to the correct UK/EU setting.

13. Open **Experimental Settings** and set the following:

    - **Default Scope:** `sco`
    - **Default Hash Size:** `3 byte`

14. Save or apply the settings.

15. Reboot the companion node if the app asks you to do so.

16. Reconnect to the companion node by Bluetooth after it restarts.

17. Confirm the **Default Scope** is still set to `sco`.

18. Confirm the **Default Hash Size** is still set to `3 byte`.

19. Open the ScotMesh public channel.

20. Send a short test message, for example:

    `Test from newly configured ScotMesh companion node`

21. Confirm that the message sends successfully.

Once these steps are complete, the companion node should be connected to ScotMesh and ready to send messages using the Scottish default scope.




> The default scope is the most important setting on ScotMesh. Without it, your messages may not travel anywhere useful on our network.
{.is-warning}






## 💬 4. Send your first message in the #scotland channel.

1. In the app, open or create a channel called `#scotland`.
2. Check the channel scope is set to `sco`. If the app shows a scope option, make sure it says `sco`.
3. Type a short hello and send it.

That is all you need to do. If there is a repeater nearby, your message should travel through the mesh.

## 🤔 5. Nothing coming back?

Do not worry — this is normal at first.

- **Check your scope.** Go back to step 2 and confirm `sco` is set as the default and on the `#scotland` channel.
- **Check repeater coverage.** It is best **NOT TO USE** [MeshCore Node Map](https://map.meshcore.io/) to see if there are any repeaters near you. It is not up to date and can give false promise of coverage. Use the discover nearby nodes Scanner in the Meshcore app tools.
> The web map is inaccurate and alway out of date. The companion app map will be empty until it hears adverts. the only way to reliably check for repeaters is to use the repeater search tool in the companion app
- **Try `#test`.** Send a message in a channel called `#test` with scope `sco` — this is what the community uses for testing. If someone else is active they may respond.
- **Ask for help.** The [Discord](https://discord.gg/invite/VvagXJn7Bq) is friendly and someone will help you work out what is happening.

## 🗺️ Where to go next

Once you are up and running:

- [Scopes](https://wiki.scotmesh.uk/en/MeshCore/scopes) explains what scope means and how to set it properly for different channels.
- [Channels](/meshcore/channels) lists the agreed community channels and what scope to use with each.
- [Repeater Quick Setup](https://wiki.scotmesh.uk/en/MeshCore/repeater-quick-setup) is for you if you want to set up a repeater and help the network grow.
