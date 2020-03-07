In this guide: 
* [Quick Setup Instructions](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#quick-setup-instructions)
* [Streaming over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#streaming-over-the-internet)
* [Moonlight Client Setup Instructions](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#moonlight-client-setup-instructions)
* [Keyboard/Mouse/Gamepad Input Options](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#keyboardmousegamepad-input-Options)
* [Adding custom programs that are not automatically found](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found)
* [Using Moonlight to stream your entire desktop](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-moonlight-to-stream-your-entire-desktop)
* [Troubleshooting](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#troubleshooting)

***

**Host Gaming PC Requirements** 

* NVIDIA GeForce GTX/RTX 600+ series GPU (GT-series and AMD GPUs aren't supported by NVIDIA GameStream)
* NVIDIA GeForce Experience (GFE) 2.1.1 or higher
* 720p or higher display (or headless display dongle) connected to the GeForce GPU
* 5 Mbps or higher upload speed (only required for streaming outside your house)

## Quick Setup Instructions
1. On your gaming PC, install the [GeForce Experience software](https://www.nvidia.com/en-us/geforce/geforce-experience/) from NVIDIA. Your PC may need a reboot after installation to finish setup.

2. Start GeForce Experience and click on the **Settings "gear" button**. Then choose the **SHIELD** option. Make sure the GameStream switch is in the **"on" position (green)**. If the SHIELD tab is not present, see the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

  <p align="center">
     <img src="https://github.com/moonlight-stream/moonlight-docs/wiki/images/gfe-gamestream-enable-small.png"/>
  </p>

3. Start Moonlight and make sure your client is connected to the same network as your PC. In most cases, your gaming PC will show up automatically in the PC list after a few seconds. Click the entry in the PC list to start pairing.

4. On your PC, enter the PIN displayed in Moonlight and accept the pairing dialog. If you don't see a pairing dialog, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

5. Try streaming a game or app to make sure everything is working. If you encounter issues, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

## Streaming over the Internet

### Automatic configuration (recommended for most users)
For the easiest possible setup process, we highly recommend that you **first pair Moonlight with your gaming PC while connected to your home network** before trying to use Moonlight over the Internet.

#### If your gaming PC is already paired with Moonlight:
1. Install the [Moonlight Internet Hosting Tool](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) on your gaming PC.
2. Run "Moonlight Internet Streaming Tester" via the Start Menu to confirm it's working properly.

#### If your gaming PC is _not_ already paired with Moonlight:
1. Install the [Moonlight Internet Hosting Tool](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) on your gaming PC.
2. Run "Moonlight Internet Streaming Tester" via the Start Menu.
3. Type the IP address that is displayed on the tester's success dialog into the Add PC dialog of Moonlight.
    * You must ensure your Moonlight client is **not connected to the same network as your gaming PC** during this step or the connection may not be successful.

#### Having trouble?
* Ensure UPnP is enabled in your router settings and delete any older Moonlight port forwarding entries.

* Try streaming from a different network. Some corporate or public WiFi networks block streaming applications like Moonlight. If that happens, you may have success with the ZeroTier setup steps below.

* Run the "Moonlight Internet Streaming Tester" found in the [Moonlight Internet Hosting Tool](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) and ask for help on our [Discord server](https://moonlight-stream.org/discord). Be sure to have the tester log handy. 

### ZeroTier
[ZeroTier](https://www.zerotier.com/) which is a service that acts similar to a VPN, but with better performance in most cases.

This option also gives you the ability to stream from multiple PCs that are all connected via a single Internet connection. However, it requires software on your hosts and clients that must be running and connected in order to stream over the Internet, unlike the other Internet streaming options.

You should use ZeroTier if you are in one of the following situations:
* The automatic tool above says you're behind a Carrier-Grade NAT, that you have two routers connected together, or otherwise doesn't work and you can't resolve it yourself.
* You have multiple gaming PCs on your network that you'd like to stream from over the Internet.
* Moonlight is blocked on the network you want to use for streaming.

To set it up:
1. [Create an account](https://my.zerotier.com/login) on the ZeroTier website. The free service is perfectly fine for Moonlight.
2. Download the Windows version for your PC from the [Downloads page](http://www.zerotier.com/download.shtml) and install it on your host gaming PC.
3. Install ZeroTier on your client device.
    * If using Moonlight on a PC or Mac, download and install the appropriate version from the [Downloads page](http://www.zerotier.com/download.shtml).
    * If using Moonlight on Android or iOS, the apps are available on the [Google Play Store](https://play.google.com/store/apps/details?id=com.zerotier.one) and [Apple App Store](https://itunes.apple.com/us/app/zerotier-one/id1084101492).
4. Go to the [Networks tab](https://my.zerotier.com/network) then create a new network.
    * Uncheck all checkboxes in the "IPv6 Auto-Assign" section (if checked)
    * Under the "IPv4 Auto-Assign" section, ensure "Auto-Assign from Range" is checked, click the "Easy" button, then choose "10.147.17.*"
5. Copy the Network ID from that page and type it into the ZeroTier app's Join Network dialog (or use the e-mail invite system).
    * If you get a prompt from Windows about asking for the network type/location, choose Private or Home network to avoid firewall issues.
6. After joining the network on each device (_including your client running Moonlight!_), go back to the ZeroTier Network page and check the Auth checkbox for each member of your network to allow the devices to connect with each other. ZeroTier should show up as connected on all devices.
7. With ZeroTier connected on your client and host PC, open Moonlight and click/tap the Add PC button, then type the "Managed IP" of your host PC as shown on the ZeroTier Network page.

To connect additional clients or host PCs, just download ZeroTier on the device, then complete steps 5-7.

Don't forget to connect to your ZeroTier network when you want to stream over the Internet!

### Manual port forwarding (advanced)
If the automatic tool doesn't work, you can try manually forwarding the following ports through your router to your host gaming PC's IP address for streaming to work over the Internet:
* **TCP** 47984, 47989, 48010
* **UDP** 47998, 47999, 48000, 48010

If your router has separate options for "internal port" and "external port", you should set them to the same values. For example, your port forward for TCP 47989 would be set as internal port 47989 and external port 47989.

To verify the basic port forwarding was done correctly, visit http://www.canyouseeme.org/ and test port 47984 and 47989. If port forwarding is working, they should both report "Success" when you test them. The other ports are only active during streaming, so the only way to test them is via Moonlight.

If Moonlight already found your gaming PC automatically while on the same network, it should connect to your PC over the Internet without any additional steps. If you're not on the same network as your PC, go to http://www.whatsmyip.org/ from your gaming PC, then enter the IP address you get there into Moonlight. If you don't get an error, you should be all set.

### IPv6 (advanced - certain ISPs only)

If you are lucky enough to have native IPv6 connectivity to your host gaming PC, you may opt to use IPv6 for Internet streaming. This option is only recommended for those very familiar with network administration. You may combine these steps with the Moonlight Internet Hosting Tool above to stream over IPv4 or IPv6, depending on your client's connectivity.

1. Navigate to http://test-ipv6.com/ on both your host gaming PC and client device/PC to check their IPv6 test scores. You may need to disable Chrome's Data Compression option to get accurate results on mobile.

    * If your host PC scores 0/10, check your router settings for an IPv6 option. Make sure it's enabled and set to "Native", "Automatic", "DHCPv6", or similar. Avoid "6to4" or "Teredo" options. Restart your router and try the IPv6 test again. If you can't find an IPv6 option or it's not working, contact your ISP and ask whether they support IPv6.

    * If you can't get your host gaming PC to 10/10, you won't be able to use this method for streaming over the Internet with your ISP.

    * If your client device doesn't score 10/10 but your host PC does, you can try the [Cloudflare 1.1.1.1 app for iOS and Android](https://1.1.1.1/) with the free 'WARP' feature to gain IPv6 connectivity on networks that don't natively support it.

2. Install the [GameStream IPv6 Forwarder](https://github.com/moonlight-stream/GS-IPv6-Forwarder#instructions) on your host gaming PC (same PC that runs GeForce Experience). This step is only required if you do not have the [Moonlight Internet Hosting Tool](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) already installed.

3. If Moonlight already found your gaming PC automatically while on the same network, it should connect to your PC over IPv6 without any additional steps. If you haven't already paired to your gaming PC while on the same network, click Add PC and type the IPv6 address of your host gaming PC.

All officially supported Moonlight clients (iOS/tvOS, PC, Android) support streaming from servers over IPv6. Unofficial clients (Embedded, Vita) may not.

## Firewall setup

If you are not able to stream when connected to the same network as your gaming PC, you may need to add firewall rules to stream successfully. First, try disabling the firewall software on your gaming PC (usually Windows Firewall or a firewall integrated into your anti-virus software) to confirm it's a firewall-related problem.

### Windows Firewall
GeForce Experience should create rules for Windows Firewall automatically, but in the event that they don't work, you can create the rules required to host streaming by using the following steps:
1. Open a Command Prompt or PowerShell window as administrator
2. Run the following 2 commands:
```
netsh advfirewall firewall add rule name="GameStream UDP" dir=in protocol=udp localport=5353,47998-48010 action=allow
netsh advfirewall firewall add rule name="GameStream TCP" dir=in protocol=tcp localport=47984,47989,48010 action=allow
```
3. Ensure your PC now appears online in Moonlight

### Other firewall software
For other firewall products, you should follow their instructions to create exceptions for the following ports:
* **TCP** 47984, 47989, 48010
* **UDP** 5353, 47998, 47999, 48000, 48002, 48010

## Moonlight Client Setup Instructions
**Client Requirements**

* Android: An Android device running Android 4.1 (Jelly Bean) or newer. Newer and "flagship" devices with higher processor speeds are more likely to be able to handle Moonlight well by using the hardware video system on the device to produce smooth streaming without video stuttering or freezing.

* iOS: An iOS device running iOS 8.0 or later.

* tvOS: An Apple TV device running tvOS 12.0 or later.

* PC: Windows 7+, macOS 10.13+, or Linux. Your PC should be new enough that it supports hardware-accelerated H.264 video decoding, otherwise it will have to use CPU decoding. Most PCs made since around 2010 should work fine, though older PCs may not be able to stream at 60 FPS without lag.

* ChromeOS: All ChromeOS devices should have the required hardware.

**Internet and Network Requirements**

To have a good experience, you need a mid to high-end wireless router with a good wireless connection to your client device (5 Gigahertz (GHz) highly recommended, Wireless-N (802.11n) or better strongly recommended) and a good connection from your PC server to your router (Ethernet/wired connections highly recommended).

## Keyboard/Mouse/Gamepad Input Options

**PC client**

PC clients support keyboard, mouse, and touchscreen input and up to 4 game controllers (with mappings for most common gamepads included).

* Ctrl+Alt+Shift+Z - Toggle mouse pointer capture
* Ctrl+Alt+Shift+X - Toggle between full-screen and windowed mode
* Ctrl+Alt+Shift+Q - Quit the streaming session (leaving the game running on the host PC)
* Ctrl+Alt+Shift+S - Open performance stats overlay

**Touchscreen controls**

Moonlight for Android, iOS, and PC use the touch screen as a way of controlling the mouse cursor. Multi-touch devices can emulate more mouse functions than single-touch devices.

* Swiping across the screen moves the mouse cursor in the direction of the swipe.
* Tap once with one finger to left-click.
* Tap and hold in the same place to start a click and drag. After a short while, swipe the finger to drag in the direction of the swipe.
* Hold one finger down and tap a second finger to right-click.
* Tap with three fingers to open the on-screen keyboard (Android and iOS only).
* Scroll vertically by dragging with 2 fingers (iOS only for now).

**Android client**

Moonlight supports gamepads that use the standard Android button mapping. It also supports some popular non-Android controllers like the Xbox 360, Xbox One, PS3, and PS4 controllers. However, we recommend testing these with your specific Android device first, because some controllers have latency or disconnection issues (particularly with PlayStation controllers over Bluetooth).

For non-SHIELD devices and devices running Android 7.1 (Nougat) or earlier, using an external mouse with proper mouse capture on Android requires a rooted device. If you want to use an external mouse on your rooted device, you should download `app-root-release.apk` from the [GitHub releases page](https://github.com/moonlight-stream/moonlight-android/releases). NVIDIA SHIELD devices and Android 8.0 (Oreo) have mouse capturing built-in that Moonlight uses without needing root. Moonlight for Rooted Devices is not available for Android 8.0, since the non-root version contains all features that required root using the new Android Oreo APIs.

To toggle capturing the mouse cursor on Moonlight for Rooted Devices, press Ctrl+Alt+Z.

If you don't have a mouse connected to your Android device, you can emulate one using a game controller. Press and hold the Start button to toggle mouse emulation. When mouse emulation is on, you can use either analog stick to move the cursor. The A button left clicks and the B button right clicks.

**iOS/tvOS client**

If your device is running iOS/tvOS 13 or later, you can use Xbox One S and PS4 controllers with your device over Bluetooth. Moonlight supports all physical buttons on these controllers, including Select, L3, and R3. You can also still use MFi controllers if you want, but they may not have all of the buttons that an Xbox or PS4 controller has.

Devices running iOS/tvOS 12 or earlier are limited to MFi controllers. We recommend the "extended layout" controllers which have most buttons present on a typical Xbox controller. Notably lacking on most MFi controllers are the L3 and R3 buttons and the Select button. When using the Auto setting for on-screen controls on iOS, an overlay will be displayed containing the buttons that your physical controller is missing.

You can use the Apple TV remote as a touchpad to move the mouse cursor and click.

To disconnect from your PC while streaming on iOS, swipe from the left edge of the screen. To disconnect on tvOS, double-tap the Menu button on your Apple TV Remote or press the Xbox/PS button on your gamepad.

iCade gamepads (old iOS gamepads that fake a Bluetooth keyboard) are not supported by Moonlight.

## Adding custom programs that are not automatically found
You can stream any almost any game or app by adding the EXE file to GFE manually (if it's not found by the automatic app scan). Open GeForce Experience, click the **Settings (gear) button**, click **SHIELD** on the sidebar, then click the **Add button** on the right. Browse to the app or file you want to add and click OK. You can rename the app using the **Edit button**.

The next time the client opens and displays the App List, the newly added programs and games should be displayed and ready to stream.

If quitting an application doesn't stop Moonlight, press *Ctrl+Shift+Alt+Q* on Moonlight PC to quit the streaming session. On Moonlight Android and iOS, pressing the home key will switch out of the streaming session. Choose the **Quit Session** option from the App List to fully quit the streaming session. 

## Using Moonlight to stream your entire desktop
Follow the steps above for adding a custom program, but for the path use: **C:\windows\system32\mstsc.exe**

You can rename the remote desktop entry using the Edit button. When you click this entry, you will see your full desktop where you can run whatever you want.

Even though the mstsc.exe executable is typically used for Microsoft Remote Desktop, this is only an indicator to GeForce Experience that you want to stream your desktop. It does not actually launch mstsc.exe or use RDP to stream.

## Troubleshooting

See our [dedicated troubleshooting wiki page](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting) for detailed steps for resolving a variety of issues.

If the information on the wiki doesn't help you, you can join our [Discord server](https://moonlight-stream.org/discord) to get help from the developers and the community. This is the recommended way to get the fastest help, since many people can answer your questions.

If you don't want to use Discord, you can email info@moonlight-stream.org but be aware that responses may be delayed, since this only goes to core developers. Please ensure you include all necessary information, including GeForce Experience and driver versions, specifications of your client device, streaming settings, etc.

***
