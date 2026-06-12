---
title: Upgrading MeshCore Repeaters Using OTA
description: Instructions for proximity updating firmwar
published: true
date: 2026-06-12T18:00:26.272Z
tags: meshcore, firmware
editor: markdown
dateCreated: 2026-06-12T16:47:05.172Z
---

# Upgrading MeshCore Repeaters Using OTA

This guide explains how to upgrade a MeshCore repeater or room server using the OTA function.

OTA means **Over The Air**. It allows firmware to be upgraded without physically connecting the repeater to a computer by USB. This is useful for repeaters already installed on roofs, masts, poles, lofts or other awkward locations.

> **Important:** OTA is convenient, but it still carries some risk. Make sure you use the correct firmware for the correct hardware.

---

## Supported OTA methods

There are two common OTA methods depending on the hardware type:

| Hardware type | Common examples | OTA method |
|---|---|---|
| nRF52 devices | RAK4631, Heltec T114, Seeed XIAO nRF52840, SenseCAP nRF devices | Bluetooth DFU using the **nRF Device Firmware Update** app |
| ESP32 devices | Heltec V3, some ESP32 repeaters/room servers | Temporary Wi-Fi access point called **MeshCore OTA** |

If you are not sure which method applies, check the device hardware before starting.

---

## Before you start

Before upgrading, make sure you have:

- Admin access to the repeater or room server.
- A recent copy or screenshot of the repeater settings.
- The correct firmware for the exact hardware model.
- A phone or tablet with Bluetooth enabled for nRF devices.
- Good battery level on your phone.
- The repeater has enough power to complete the update.
- You are physically close enough for a reliable Bluetooth or Wi-Fi connection.

For solar repeaters, avoid doing OTA updates when the battery is low or the weather is poor.

---

## Firmware file warning

When downloading firmware, make sure you select the correct file.

### For nRF52 OTA updates

Use the firmware **ZIP** file intended for DFU / OTA update.

Do **not** unzip it unless the instructions for your specific device say otherwise.

### For ESP32 OTA updates

Use the firmware file that does **not** contain `merged` in the filename.

> **Do not use a merged firmware file for OTA.**
>
> A merged firmware file is normally for a full USB flash and may wipe or reset the device.

---

## Download the firmware

1. Go to the MeshCore flasher:

   https://flasher.meshcore.io

2. Select the correct device type.

3. Select the correct role, usually:

   - `Repeater`
   - `Room Server`
   - `Room Server / Repeater`

4. Download the correct firmware file for your hardware.

5. Save the file somewhere easy to find on your phone or computer.

---

# Method 1: OTA update for nRF52 devices

Use this method for devices such as:

- RAK4631
- Heltec T114
- Seeed XIAO nRF52840
- SenseCAP nRF-based devices

---

## Step 1 — Install the DFU app

Install the Nordic **nRF Device Firmware Update** app.

- iOS: search the App Store for `nRF Device Firmware Update`
- Android: search Google Play for `nRF Device Firmware Update`

---

## Step 2 — Connect to the repeater in MeshCore

1. Open the MeshCore app.

2. Connect to the repeater or room server.

3. Log in using the admin password.

4. Open the repeater management screen.

5. Open the command line / terminal.

---

## Step 3 — Put the repeater into OTA mode

In the MeshCore command line, enter:

```text
start ota
```

The device should reply:

```text
OK
```

The repeater is now in OTA / DFU mode.

Leave the repeater powered on and do not restart it while you move to the DFU app.

## Step 4 — Configure the DFU app

Open the **nRF Device Firmware Update** app.

Recommended settings:

- Enable **Packets receipt notifications**
- Set the number of packets to:

| Device | Packet setting |
|---|---|
| RAK4631 | 10 |
| Heltec T114 | 8 |

If unsure, use `8` as a safe value.

---

## Step 5 — Select the firmware file

In the **nRF Device Firmware Update** app:

1. Select the firmware ZIP file you downloaded.
2. Scan for nearby DFU devices.
3. Select the repeater.

The device may appear as a DFU device rather than by its normal MeshCore name.

If the device does not appear:

- Make sure Bluetooth is enabled.
- Move closer to the repeater.
- Re-run the MeshCore command: `start ota`
- Try enabling **Force Scanning** in the DFU app if available.
- Toggle Bluetooth off and on.
- Restart the phone if needed.

---

## Step 6 — Start the upload

Press **Upload** in the DFU app.

Keep the phone awake and close to the repeater until the update finishes.

Do not:

- Leave the app.
- Lock the phone.
- Walk away from the repeater.
- Turn Bluetooth off.
- Power off the repeater.

The update can take a few minutes.

---

## Step 7 — Wait for reboot

When the upload completes, the repeater should reboot automatically.

Wait a minute or two before trying to reconnect.

---

## Step 8 — Confirm the upgrade

Reconnect to the repeater in the MeshCore app.

Check the firmware version from the management screen or command line.

Also check that the repeater settings are still correct, especially:

- Region / scope settings
- Default scope
- Repeater enabled
- Advert settings
- Flood settings
- TX power
- Admin access
- GPS/location settings if used

---

# Method 2: OTA update for ESP32 devices

Use this method for ESP32-based MeshCore repeaters or room servers.

---

## Step 1 — Connect to the repeater in MeshCore

1. Open the MeshCore app.
2. Connect to the repeater or room server.
3. Log in using the admin password.
4. Open the repeater command line / terminal.

---

## Step 2 — Start OTA mode

Enter the following command:

`start ota`

The ESP32 device should start a temporary Wi-Fi access point called something like:

`MeshCore OTA`

---

## Step 3 — Connect to the OTA Wi-Fi

On your phone, tablet or laptop:

1. Open Wi-Fi settings.
2. Connect to the temporary Wi-Fi network:

`MeshCore OTA`

3. Stay connected to this Wi-Fi until the upload is complete.

---

## Step 4 — Open the OTA upload page

Open a web browser and go to:

`http://192.168.4.1/update`

If the CLI shows a different IP address, use the IP address shown by the device.

---

## Step 5 — Upload the firmware

1. Choose the firmware file.
2. Make sure the file is the correct one for your hardware.
3. Make sure the filename does **not** contain `merged`.
4. Upload the file.
5. Wait until the update completes.

Do not disconnect from the `MeshCore OTA` Wi-Fi while the upload is running.

> **Important:** Do not use a merged firmware file for ESP32 OTA updates.  
> A merged firmware file is normally for a full USB flash and may wipe or reset the device.

---

## Step 6 — Wait for reboot and confirm

After upload, the device should reboot.

Reconnect through the MeshCore app and confirm:

- Firmware version
- Repeater settings
- Region / scope settings
- Admin access
- TX power
- Advert and flood settings

---

# Scot Mesh post-upgrade checks

After upgrading a Scot Mesh repeater, check the following before leaving it alone.

## Basic checks

- Repeater is online
- Repeater can be seen by nearby nodes
- Admin access still works
- Firmware version is correct
- Time/location information looks correct if used

---

## Region and scope checks

For Scot Mesh, confirm the repeater still has the correct region configuration.

Typical Scot Mesh structure:

| Code | Region |
|---|---|
| `sco` | Scotland |
| `cen` | Central Scotland |
| `fal` | Falkirk |
| `ioi` | Island of Ireland neighbour region |

Check that the repeater has the correct local and parent regions for its area.

Also confirm that wildcard / unrestricted flooding has not been accidentally restored.

---

## Recommended Scot Mesh settings to re-check

The exact settings may vary by repeater, but these are worth checking after any firmware upgrade:

- Default scope
- Region list
- Region parent relationships
- Region flood permissions
- Wildcard flood deny
- Repeater enabled
- TX power
- Flood max
- Advert interval
- Flood advert interval
- Path hash size / routing byte size

If the repeater was part of the Scot Mesh scoped region rollout, do not assume these settings survived the upgrade. Check them.

---

# Troubleshooting

## The repeater does not appear in the DFU app

Try the following:

- Move closer to the repeater.
- Run `start ota` again.
- Turn Bluetooth off and on.
- Enable **Force Scanning** in the DFU app.
- Restart the phone.
- Power-cycle the repeater if safe to do so.

---

## The update stalls

Do not immediately power-cycle the repeater.

First:

- Keep the phone close.
- Keep the app open.
- Wait a few minutes.
- Check that Bluetooth or Wi-Fi is still connected.

If it has clearly failed:

- Close the DFU app.
- Toggle Bluetooth off and on.
- Restart the phone if needed.
- Reconnect to the repeater if possible.
- Run `start ota` again.
- Retry the upload.

---

## The phone locked during the update

If the update has stopped progressing:

- Unlock the phone.
- Return to the DFU app.
- Check whether the upload resumes.

If it does not resume, restart the OTA process.

For future updates, keep the phone awake and the DFU app in the foreground.

---

## The repeater does not come back after OTA

Possible causes:

- Wrong firmware file
- Power loss during update
- Bluetooth/Wi-Fi upload failure
- Bootloader issue

Try:

- Wait a few minutes.
- Scan again in the MeshCore app.
- Scan again in the DFU app.
- Power-cycle the repeater if safe.
- Try the OTA process again if the device still appears in DFU mode.

If the device no longer appears in MeshCore or DFU mode, it may need a physical USB recovery flash.

---

# Good practice

Before updating an important repeater:

- Update one test device first.
- Keep a copy of the old known-good firmware.
- Take screenshots of important settings.
- Avoid updating multiple key repeaters at the same time.
- Avoid updating during poor weather if solar powered.
- Avoid updating when the network is busy.
- Tell local users before upgrading a major repeater.

For hilltop or difficult-access repeaters, consider fitting or confirming an OTA-capable bootloader before deployment.

---

# Summary

The normal OTA process is:

1. Download the correct firmware.
2. Connect to the repeater as admin.
3. Open the command line.
4. Run `start ota`.
5. Use the DFU app for nRF52 devices.
6. Use the MeshCore OTA Wi-Fi page for ESP32 devices.
7. Wait for reboot.
8. Confirm firmware and settings.

OTA makes repeater maintenance much easier, but always check the firmware file and confirm the repeater settings afterwards.