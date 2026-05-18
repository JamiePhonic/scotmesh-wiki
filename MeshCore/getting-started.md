---
title: Getting Started with ScotMesh
description: A friendly beginner guide for new ScotMesh MeshCore users — from unboxing to sending your first message.
published: true
date: 2026-05-18T22:28:00.000Z
tags: meshcore, scotland, beginner, getting-started
editor: markdown
dateCreated: 2026-05-18T22:28:00.000Z
---

# Getting Started with ScotMesh

Welcome. This page is for people who are brand new to ScotMesh and MeshCore. You do not need to know anything about radio or networking to follow this guide.

> This guide is written for **companion node** devices — small LoRa radios that pair with the MeshCore Companion App on your phone. More capable standalone devices do exist, but those are out of scope for this guide. If you are setting one of those up, ask in the [Discord](https://discord.gg/invite/VvagXJn7Bq) for advice.
{.is-info}

## What is ScotMesh?

ScotMesh is a community radio messaging network across Scotland. It uses small, low-power LoRa radios to carry short messages between people — no mobile network, no Wi-Fi, no internet required.

Think of it like a local text messaging service that works off-grid, powered by volunteer-run repeaters dotted across the country.

## What you need

- A MeshCore **companion node** — a small LoRa radio that pairs with your phone over Bluetooth.
- A smartphone — Android or iPhone both work.
- That is it.

> Not sure which companion node to get? Ask in the [Discord](https://discord.gg/invite/VvagXJn7Bq) and the community can point you in the right direction.
{.is-info}

## 1. Get the app

Download the **MeshCore Companion App** on your phone.

- **Android:** [MeshCore on Google Play](https://play.google.com/store/search?q=meshcore)
- **iPhone:** [MeshCore on the App Store](https://apps.apple.com/search?term=meshcore)

Open the app once it has installed.

## 2. Connect your device

1. Make sure your LoRa device is powered on.
2. In the app, tap **Add Device** or the connect button.
3. The app will search for nearby devices over Bluetooth. Select yours from the list.
4. Wait a moment for it to connect. You should see your device appear in the app.

> If the device does not show up, make sure Bluetooth is enabled on your phone and that the device is in pairing mode. Check your device's instructions if you are unsure.
{.is-info}

## 3. One important setting

Before you send anything, set your **default scope** to `sco`. This makes sure your messages are correctly routed on the Scottish mesh.

1. Open the app menu.
2. Go to **Experimental Settings**.
3. Find **Default Scope Region** and set it to `sco`.

> This is the most important setting on ScotMesh. Without it, your messages may not travel anywhere useful on our network.
{.is-warning}

## 4. Send your first message

1. In the app, open or create a channel called `#scotland`.
2. Check the channel scope is set to `sco`. If the app shows a scope option, make sure it says `sco`.
3. Type a short hello and send it.

That is all you need to do. If there is a repeater nearby, your message should travel through the mesh.

## 5. Nothing coming back?

Do not worry — this is normal at first.

- **Check your scope.** Go back to step 3 and confirm `sco` is set as the default and on the `#scotland` channel.
- **Check repeater coverage.** Have a look at the [MeshCore Node Map](https://map.meshcore.io/) to see if there are any repeaters near you.
- **Try `#test`.** Send a message in a channel called `#test` with scope `sco` — this is what the community uses for testing. If someone else is active they may respond.
- **Ask for help.** The [Discord](https://discord.gg/invite/VvagXJn7Bq) is friendly and someone will help you work out what is happening.

## Where to go next

Once you are up and running:

- [Scopes](scopes) explains what scope means and how to set it properly for different channels.
- [Channels](channels) lists the agreed community channels and what scope to use with each.
- [Repeater Quick Setup](repeater-quick-setup) is for you if you want to set up a repeater and help the network grow.
