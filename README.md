# Wireless-USB-OC

Drivers for Realtek 802.11n and 802.11ac USB Wi-Fi adapters on macOS (10.13 till 13.1)

## Why this repo?

I wanna make a premise: I appreciate the effort of [chris1111](https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter) to create an application, but unexperienced users may have issues especially with disabling SIP policy.

This guide aims helping users who may have doubts on how his installer works.

## Compatibility

- Acer UWA5
- Alfa AWUS036AC
- Alfa AWUS036ACH
- Archer T2U Nano
- Archer T3U
- Archer T3U Plus
- Archer T2U MINI V3
- ArcherT4U V1, V2, V3
- Archer T9UH V2
- ASUS USB AC68
- ASUS USB-N13
- ASUS USB Nano-AC53
- COMFAST CF-811AC
- COMFAST CF-812AC
- Comfast CF-WU810N
- Comfast CF-758F
- Cudy WU1300S
- Cudy WU700
- DLink DWA-121 N150
- D-Link DWA-131
- EDIMAX EW-7611UCB
- EDIMAX EW-7722UTn V2
- EDIMAX_EW-7822ULC
- EDIMAX EW-7833UAC
- EDIMAX EW-7612Uan V2
- EDIMAX N300
- EDIMAX EW-7811Un (N150)
- EDUP EP-AC1689
- Fenvi AC1300 (RTL8812bu)
- FILOWA USB WiFi-RTL8812BU
- Foktech AC600 Nano
- Jensen Eagle 100-AC
- Kextech MINI USB RTL8192
- Linksys WUSB6300 V2
- Linksys WUSB6400M
- Netgear A6100
- Netgear A7000
- Netis WF2120 N Nano USB
- M-Tech UW-01 USB
- Plexgear AC1200
- Sitecom WLA7100
- TL-WN823Nv2/v3
- TL-WN725Nv3
- TL-WN723Nv2/v3
- TL-WN722Nv2/v3
- TL-WN821Nv6
- TL-WN822Nv4/v5
- TENDA W311-MINI
- TENDA U12
- TRENDnet N150 Micro
- TRENDnet TEW-808UBM
- TRENDnet TEW-908UB
- YUNCLOUD Realtek (RTL8814AU)
- ZAPO W58L (RTL881lAU)
## Requirements

- Reading
- Some patience


## Step 1: Copy the kexts in OC EFI

As most of hackintosh/OpenCore users should know, KEXTs are like Windows drivers: they make devices work on macOS.
Before people used to inject kexts directly in `/Library/Extensions` or worse in `/System/Library/Extensions` by disabling SIP, which definitely breaks the purpose of a vanilla installation.

Using bootloaders, such as the good ol' Clover - if you're stuck in 1900 BC - or OpenCore - if you are a G - you can easily inject those kexts without even voiding your vanilla-sealed installation.

In the [releases](https://github.com/dreamwhite/Wireless-USB-OC/releases/latest) section you can download the kexts that you will have to add on your existing OpenCore EFI under `EFI/OC/Kexts` folder (you don't say, uh?).

I'll leave here the copy-n-paste code for those who use text based editors:

```xml
<dict>
    <key>Arch</key>
    <string>x86_64</string>
    <key>BundlePath</key>
    <string>RtWlanU.kext</string>
    <key>Comment</key>
    <string></string>
    <key>Enabled</key>
    <true/>
    <key>ExecutablePath</key>
    <string>Contents/MacOS/RtWlanU</string>
    <key>MaxKernel</key>
    <string></string>
    <key>MinKernel</key>
    <string></string>
    <key>PlistPath</key>
    <string>Contents/Info.plist</string>
</dict>
<dict>
    <key>Arch</key>
    <string>x86_64</string>
    <key>BundlePath</key>
    <string>RtWlanU1827.kext</string>
    <key>Comment</key>
    <string></string>
    <key>Enabled</key>
    <true/>
    <key>ExecutablePath</key>
    <string>Contents/MacOS/RtWlanU1827</string>
    <key>MaxKernel</key>
    <string></string>
    <key>MinKernel</key>
    <string></string>
    <key>PlistPath</key>
    <string>Contents/Info.plist</string>
</dict>
```

## Step 2: Installing the helper utility

The official utility is shipped with a status bar helper utility which lets you connect to Wi-Fi networks.
In the [releases](https://github.com/dreamwhite/Wireless-USB-OC/releases/latest) section you can download the utility that you will have to copy under `/Applications`.

Please note that in case you receive an error message while opening the utility like `The application is damaged` most of the times it's just a matter of Apple quarantine protection which falsely flags the application as damaged.

To fix this use the following command from a terminal window: `sudo xattr -d com.apple.quarantine /Applications/StatusBarApp.app`

## Step 3: Auto launch the application on login

Probably that's the easiest step among the other ones: under `System Preferences -> Users & Groups -> Login Items` add the helper utility application.

That's all

# Credits

- [chris1111](https://github.com/chris1111) for his utility


