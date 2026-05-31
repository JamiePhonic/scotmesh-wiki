---
title: Getting Started with ScotMesh
description: A friendly beginner guide for new ScotMesh MeshCore users — from unboxing to sending your first message.
published: false
date: 2026-05-31T17:24:00.475Z
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


> For this setting, understanding the regional framework is important because it defines how traffic is organised and routed across the mesh. Regions (set on repeater nodes) allow the wider mesh to be split into sensible geographic areas, helping messages, adverts, and repeater traffic stay relevant to the area they are intended for while still allowing agreed neighbouring regions to interconnect where required. Setting the **default scope** tells the node which region it should use automatically when sending or repeating traffic that does not already have a specific scope applied. In practice, this helps keep local traffic local, reduces unnecessary flooding across unrelated areas, and improves the reliability and manageability of the mesh.


Before you can send anything from your companion app, you need to set it up for use in the ScotMesh MC mesh.

## ScotMesh CLI Settings (example location Falkirk)


1. Check the current firmware version first. The node should be running firmware that supports regional scope/default scope.

   Command: `ver`

2. Check the current region list before making changes.

   Command: `region`

3. Add the Scotland top-level region.

   Command: `region put sco`

4. Add the Central Scotland region under Scotland.

   Command: `region put cen sco`

5. Add the Falkirk area region under Central Scotland.

   Command: `region put fal cen`

6. Add the neighbouring Island of Ireland region.

   Command: `region put ioi`

7. Allow flood traffic for the Scotland region.

   Command: `region allowf sco`

8. Allow flood traffic for the Central Scotland region.

   Command: `region allowf cen`

9. Allow flood traffic for the Falkirk area region.

   Command: `region allowf fal`

10. Allow flood traffic for the neighbouring Island of Ireland region, where required.

    Command: `region allowf ioi`

11. Deny wildcard flooding so unscoped/default legacy traffic is not flooded unnecessarily.

    Command: `region denyf *`

12. Set the companion node default scope to Scotland.

    Command: `region default sco`

13. Check that the default scope has been applied correctly.

    Command: `region default`

14. Check the final region configuration.

    Command: `region list`

15. Save the settings to the node.

    Command: `save`

16. Reboot the companion node.

    Command: `reboot`

17. After rebooting, check the firmware version again.

    Command: `ver`

18. Confirm the default scope is still set to Scotland.

    Command: `region default`

19. Confirm the regional framework is still present.

    Command: `region`

20. Send a test message and confirm it is being sent using the correct ScotMesh scope.

> This is the most important setting on ScotMesh. Without it, your messages may not travel anywhere useful on our network.
{.is-warning}


> Lots more settings to be enetered before we get to sending messgae stage e.g.  EU/UK narrow, path hash, etc etc.    if this is to flow logical as a set up guide for companion nodes we need it to flow correctly
> 



## 💬 4. Send your first message

1. In the app, open or create a channel called `#scotland`.
2. Check the channel scope is set to `sco`. If the app shows a scope option, make sure it says `sco`.
3. Type a short hello and send it.

That is all you need to do. If there is a repeater nearby, your message should travel through the mesh.

## 🤔 5. Nothing coming back?

Do not worry — this is normal at first.

- **Check your scope.** Go back to step 3 and confirm `sco` is set as the default and on the `#scotland` channel.
- ~~**Check repeater coverage.** Have a look at the [MeshCore Node Map](https://map.meshcore.io/) to see if there are any repeaters near you.~~
> The web map is inacureate and alway out of date. THe companion app map will be empty until it hears adverts. the only way to reliably check for rpeaters is to use the repeater search tool in the companion app
- **Try `#test`.** Send a message in a channel called `#test` with scope `sco` — this is what the community uses for testing. If someone else is active they may respond.
- **Ask for help.** The [Discord](https://discord.gg/invite/VvagXJn7Bq) is friendly and someone will help you work out what is happening.

## 🗺️ Where to go next

Once you are up and running:

- [Scopes](/meshcore/scopes) explains what scope means and how to set it properly for different channels.
- [Channels](/meshcore/channels) lists the agreed community channels and what scope to use with each.
- [Repeater Quick Setup](/meshcore/repeater-quick-setup) is for you if you want to set up a repeater and help the network grow.
