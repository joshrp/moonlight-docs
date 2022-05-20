<a href="https://moonlight-stream.org/discord"><img src="https://moonlight-stream.org/images/discord.png" height="70" alt="Join our Discord"></a>

* [Quick Setup Instructions](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#quick-setup-instructions)
* [Streaming over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#streaming-over-the-internet)
* [Moonlight Client Setup Instructions](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#moonlight-client-setup-instructions)
* [Additional Requirements for HDR Streaming](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#additional-requirements-for-hdr-streaming)
* [Keyboard/Mouse/Gamepad Input Options](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#keyboardmousegamepad-input-Options)
* [Adding custom programs that are not automatically found](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found)
* [Using Moonlight to stream your entire desktop](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-moonlight-to-stream-your-entire-desktop)
* [Frequently Asked Questions](https://github.com/moonlight-stream/moonlight-docs/wiki/Frequently-Asked-Questions)
* [Troubleshooting](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting)

***

**Host Gaming PC Requirements** 

* NVIDIA GeForce GTX/RTX 600+ series GPU, or NVIDIA Quadro GPU (Kepler series or later)
* NVIDIA GeForce Experience (GFE) 2.1.1 or higher, or NVIDIA Quadro Experience
* 720p or higher display (or headless display dongle) connected to the NVIDIA GPU
* 5 Mbps or higher upload speed (only required for streaming outside your house)

There are [additional host PC requirements](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#additional-requirements-for-hdr-streaming) for streaming HDR content.

## Quick Setup Instructions
1. On your gaming PC, install the [GeForce Experience software](https://www.nvidia.com/en-us/geforce/geforce-experience/) from NVIDIA. Your PC may need a reboot after installation to finish setup.
    * If your PC has a Quadro GPU, install the [Quadro Experience software](https://www.nvidia.com/en-us/design-visualization/software/quadro-experience/) instead.

2. Start GeForce/Quadro Experience and click on the **Settings "gear" button**. Then choose the **SHIELD** option. Make sure the GameStream switch is in the **"on" position (green)**. If the SHIELD tab is not present, see the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

  <p align="center">
     <img src="https://github.com/moonlight-stream/moonlight-docs/wiki/images/gfe-gamestream-enable-small.png"/>
  </p>

3. Start Moonlight and make sure your client is connected to the same network as your PC. In most cases, your gaming PC will show up automatically in the PC list after a few seconds. Click the entry in the PC list to start pairing.

4. On your PC, enter the PIN displayed in Moonlight and accept the pairing dialog. If you don't see a pairing dialog, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

5. Try streaming a game or app to make sure everything is working. If you encounter issues, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

6. If you don't see the game you want to stream in Moonlight, you can [add it manually](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found). You can also [stream your desktop](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-moonlight-to-stream-your-entire-desktop) and launch anything you want.

## Streaming over the Internet

### Automatic configuration (recommended for most users)
For the easiest possible setup process, we highly recommend that you **first pair Moonlight with your gaming PC while connected to your home network** before trying to use Moonlight over the Internet. For iOS and tvOS users, [you _must_ pair while connected to the same network](https://github.com/moonlight-stream/moonlight-ios/issues/417) to comply with Apple guidelines.

Moonlight Internet Hosting Tool must remain installed on your host PC to maintain the ability to stream over the Internet.

#### If your gaming PC is already paired with Moonlight:
1. Install the [Moonlight Internet Hosting Tool](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) on your gaming PC.
2. Run "Moonlight Internet Streaming Tester" via the Start Menu to confirm it's working properly.
3. Do not uninstall Moonlight Internet Hosting Tool, unless you no longer want to stream over the Internet. It needs to remain installed on your PC to maintain the port forwarding entries on your router.

#### If your gaming PC is _not_ already paired with Moonlight:
1. Install the [Moonlight Internet Hosting Tool](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) on your gaming PC.
2. Run "Moonlight Internet Streaming Tester" via the Start Menu.
3. Type the IP address that is displayed on the tester's success dialog into the Add PC dialog of Moonlight.
    * You must ensure your Moonlight client is **not connected to the same network as your gaming PC** during this step or the connection may not be successful.
4. Do not uninstall Moonlight Internet Hosting Tool, unless you no longer want to stream over the Internet. It needs to remain installed on your PC to maintain the port forwarding entries on your router.

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
2. Download the Windows version for your PC from the [Downloads page](https://www.zerotier.com/download.shtml) and install it on your host gaming PC.
3. Install ZeroTier on your client device.
    * If using Moonlight on a PC or Mac, download and install the appropriate version from the [Downloads page](https://www.zerotier.com/download.shtml).
    * If using Moonlight on Android or iOS, the apps are available on the [Google Play Store](https://play.google.com/store/apps/details?id=com.zerotier.one) and [Apple App Store](https://itunes.apple.com/us/app/zerotier-one/id1084101492).
4. Go to the [Networks tab](https://my.zerotier.com/network) then create a new network.
    * Uncheck all checkboxes in the "IPv6 Auto-Assign" section (if checked)
    * Under the "IPv4 Auto-Assign" section, ensure "Auto-Assign from Range" is checked, click the "Easy" button, then choose "10.147.17.*"
5. Copy the Network ID from that page and type it into the ZeroTier app's Join Network dialog (or use the e-mail invite system).
    * If you get a prompt from Windows about asking for the network type/location, choose Private or Home network to avoid firewall issues.
6. After joining the network on each device (_including your client running Moonlight!_), go back to the ZeroTier Network page and **check the Auth checkbox for each member of your network** to allow the devices to connect with each other. ZeroTier should show up as connected on all devices.
7. With ZeroTier connected on your client and host PC, open Moonlight and click/tap the Add PC button, then type the "Managed IP" of your host PC as shown on the ZeroTier Network page.

To connect additional clients or host PCs, just download ZeroTier on the device, then complete steps 5-7.

Don't forget to connect to your ZeroTier network when you want to stream over the Internet!

### Manual port forwarding (advanced)
If the automatic tool doesn't work, you can try manually forwarding the following ports through your router to your host gaming PC's IP address for streaming to work over the Internet:
* **TCP** 47984, 47989, 48010
* **UDP** 47998, 47999, 48000, 48002, 48010

If your router has separate options for "internal port" and "external port", you should set them to the same values. For example, your port forward for TCP 47989 would be set as internal port 47989 and external port 47989.

To verify the basic port forwarding was done correctly, visit https://www.canyouseeme.org/ and test port 47984 and 47989. If port forwarding is working, they should both report "Success" when you test them. The other ports are only active during streaming, so the only way to test them is via Moonlight.

If Moonlight already found your gaming PC automatically while on the same network, it should connect to your PC over the Internet without any additional steps. If you're not on the same network as your PC, go to https://www.whatsmyip.org/ from your gaming PC, then enter the IP address you get there into Moonlight. If you don't get an error, you should be all set.  
Also see [DHCP leasing](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#static-dhcp-reservation).

### Static DHCP reservation

On many routers it will also be necessary to make a static DHCP reservation to ensure the host always has the same network IP address. This makes sure the ports you have forwarded remain forwarded to the correct machine. Some routers will do this automatically when port forwarding is done. But many do not and it must be done manually. Router makers also try to make there routers “user friendly” and call this function differently such as static IP, Reservations, fixed IP and so on. They also like to put the setting in different places. Common places are DHCP settings, Client lists, and NAT/LAN settings. What your looking for is the ability to set a client to have a certain IP whether that be via MAC address or client list.

### IPv6 (advanced - certain ISPs only)

If you are lucky enough to have native IPv6 connectivity to your host gaming PC, you may opt to use IPv6 for Internet streaming. This option is only recommended for those very familiar with network administration. You may combine these steps with the Moonlight Internet Hosting Tool above to stream over IPv4 or IPv6, depending on your client's connectivity.

1. Navigate to http://test-ipv6.com/ on both your host gaming PC and client device/PC to check their IPv6 test scores. You may need to disable Chrome's Data Compression option to get accurate results on mobile.

    * If your host PC scores 0/10, check your router settings for an IPv6 option. Make sure it's enabled and set to "Native", "Automatic", "DHCPv6", or similar. Avoid "6to4" or "Teredo" options. Restart your router and try the IPv6 test again. If you can't find an IPv6 option or it's not working, contact your ISP and ask whether they support IPv6.

    * If you can't get your host gaming PC to 10/10, you won't be able to use this method for streaming over the Internet with your ISP.

    * If your client device doesn't score 10/10 but your host PC does, you can try the [Cloudflare 1.1.1.1 app for Windows, macOS, iOS, and Android](https://1.1.1.1/) with the free 'WARP' feature to gain IPv6 connectivity on networks that don't natively support it.

2. Install the [GameStream IPv6 Forwarder](https://github.com/moonlight-stream/GS-IPv6-Forwarder#instructions) on your host gaming PC (same PC that runs GeForce Experience). This step is only required if you do not have the [Moonlight Internet Hosting Tool](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) already installed.

3. If your router has an IPv6 firewall, you may need to create IPv6 firewall rules on your router to allow TCP ports 47984-48010 and UDP ports 47998-48010 through the firewall. The GameStream IPv6 Forwarder will create the rules for you if possible, but not many routers support this feature. If your IPv6 Moonlight connection is failing, this is most likely the reason.

4. If Moonlight already found your gaming PC automatically while on the same network, it should connect to your PC over IPv6 without any additional steps. If you haven't already paired to your gaming PC while on the same network, click Add PC and type the IPv6 address of your host gaming PC.

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

* iOS: An iOS device running iOS 9.3 or later.

* tvOS: An Apple TV device running tvOS 12.0 or later.

* PC: Windows 7+, macOS 10.13+, or Linux. Your PC should be new enough that it supports hardware-accelerated H.264 video decoding, otherwise it will have to use CPU decoding. Most PCs made since around 2010 should work fine, though older PCs may not be able to stream at 60 FPS without lag.

* ChromeOS: All ChromeOS devices should have the required hardware.

**Internet and Network Requirements**

To have a good experience, you need a mid to high-end wireless router with a good wireless connection to your client device (5 GHz WiFi 5 (802.11ac) or WiFi 6 (802.11ax) strongly recommended) and a good connection from your PC server to your router (Ethernet/wired connections highly recommended).

## Additional Requirements for HDR Streaming

HDR10 video streaming (beta) is supported on certain Moonlight clients as long as some hardware and software requirements are met.

If the HDR requirements are not met, the HDR option in Moonlight may appear grayed out or not appear at all.

**Host PC requirements for HDR streaming**
- NVIDIA GeForce GTX/RTX 1000-series or later
- Some newer games may require an HDR display or HDR10-compatible EDID emulator dongle connected to your host PC for HDR options to be available
- The stream resolution in Moonlight should be set to match the host PC's display resolution to prevent video scaling artifacts

**iOS and Apple TV client requirements for HDR streaming**
- iOS/tvOS 11.3 or later
- HDR10-compatible display
  - For iOS devices, this means devices with "XDR" displays
  - For Apple TV devices, the connected TV must support HDR10

**Android client requirements for HDR streaming**
- Android 7.0 or later
- HEVC Main10 hardware decoder
- HDR10-compatible display

**Windows client requirements for HDR streaming**
- Windows 10 1703 (Creators Update) or later
- HDR10-compatible display
- Client GPU must support both HEVC Main10 decoding and HDR10 output
  - For Intel GPUs, this is 7th-generation (Kaby Lake) iGPUs and later
  - For NVIDIA GPUs, this is 1000-series (Pascal) GPUs and later
  - For AMD GPUs, this is RX 400-series (Polaris) GPUs and later
- HDR toggle in Windows must be enabled for streaming in windowed mode

**macOS client requirements for HDR streaming**
- macOS Catalina or later
- See [Apple's documentation](https://support.apple.com/en-us/HT210980) for additional requirements and recommendations

**Linux client requirements for HDR streaming**
- Moonlight must be launched directly from the console, rather than within a desktop environment
  - This is required to allow Moonlight to directly configure the display for HDR
- Intel GPU (other vendors may work but are untested)
- HDR10-compatible display

**Raspberry Pi 4 requirements for HDR streaming**
- Moonlight must be launched directly from the console, rather than within a desktop environment
  - This is required to allow Moonlight to directly configure the display for HDR
- HDR10-compatible display
- See [HDR and HEVC support on the Raspberry Pi 4](https://github.com/moonlight-stream/moonlight-docs/wiki/Installing-Moonlight-Qt-on-Raspberry-Pi-4#hevc-and-hdr-support) for configuration steps

## Keyboard/Mouse/Gamepad Input Options

**PC client**

PC clients support keyboard, mouse, and touchscreen input and up to 4 game controllers (with mappings for most common gamepads included).

* Ctrl+Alt+Shift+Q - Quit the streaming session (leaving the game running on the host PC)
* Ctrl+Alt+Shift+Z - Toggle mouse and keyboard capture
* Ctrl+Alt+Shift+X - Toggle between full-screen and windowed mode
* Ctrl+Alt+Shift+S - Open performance stats overlay (not supported on Steam Link or Raspberry Pi)
* Ctrl+Alt+Shift+M - Toggle mouse mode (pointer capture or direct control)
* Ctrl+Alt+Shift+V - Type clipboard text on the host
* Ctrl+Alt+Shift+D - Minimize the stream window
* Ctrl+Alt+Shift+C - Toggle local cursor display in remote desktop mouse mode (remote cursor will always show up due to GameStream limitations)
* Ctrl+Alt+Shift+L - Toggle locking the mouse pointer to the video area (requires "Optimize mouse for remote desktop instead of games" checkbox enabled)

**Touchscreen controls**

Moonlight for Android, iOS, and PC use the touch screen as a way of controlling the mouse cursor. Multi-touch devices can emulate more mouse functions than single-touch devices. There are two modes of touchscreen operation that you can choose between in Moonlight - one uses the touchscreen as a trackpad and the other emulates direct touchscreen input. 

Trackpad mode:
* Move cursor: Swiping across the screen moves the mouse cursor in the direction of the swipe.
* Left click: Tap with one finger.
* Right click: While holding one finger down, tap a second finger.
* Click and drag: Long press with one finger, then start to drag after holding for about half a second.
* Scroll: Drag 2 fingers vertically.
* Show Keyboard: Tap with three fingers (Android and iOS only).

Touchscreen mode:
* Move cursor and left click: Tap the location where you would like to left click.
* Right click: Long press the location where you would like to right click.
* Click and drag: Tap a location and drag your finger across the screen.
* Show Keyboard: Tap with three fingers (Android and iOS only).
* Zoom: Pinch with 2 fingers (iOS only).
* Pan: Drag with 2 fingers (iOS only).

**Android client**

Moonlight supports gamepads that use the standard Android button mapping. It also supports some popular non-Android controllers like the Xbox 360, Xbox One, PS3, and PS4 controllers. However, we recommend testing these with your specific Android device first, because some controllers have latency or disconnection issues (particularly with PlayStation controllers over Bluetooth).

For non-SHIELD devices and devices running Android 7.1 (Nougat) or earlier, using an external mouse with proper mouse capture on Android requires a rooted device. If you want to use an external mouse on your rooted device, you should download `app-root-release.apk` from the [GitHub releases page](https://github.com/moonlight-stream/moonlight-android/releases). NVIDIA SHIELD devices and Android 8.0 (Oreo) have mouse capturing built-in that Moonlight uses without needing root. Moonlight for Rooted Devices is not available for Android 8.0, since the non-root version contains all features that required root using the new Android Oreo APIs.

To toggle capturing the mouse cursor on Moonlight for Rooted Devices, press Ctrl+Alt+Z.

If you don't have a mouse connected to your Android device, you can emulate one using a game controller. Press and hold the Start button to toggle mouse emulation. When mouse emulation is on, you can use either analog stick to move the cursor. The A button left clicks and the B button right clicks.

**iOS/tvOS client**

If your device is running iOS/tvOS 13 or later, you can use Xbox One S and PS4 controllers with your device over Bluetooth. Moonlight supports all physical buttons on these controllers, including Select, L3, and R3. Moonlight also supports controller vibration on these controllers with iOS/tvOS 14. You can also still use MFi controllers if you want, but they may not have all of the buttons that an Xbox or PS4 controller has and won't support vibration.

Devices running iOS/tvOS 12 or earlier are limited to MFi controllers. We recommend the "extended layout" controllers which have most buttons present on a typical Xbox controller. Notably lacking on most MFi controllers are the L3 and R3 buttons and the Select button. When using the Auto setting for on-screen controls on iOS, an overlay will be displayed containing the buttons that your physical controller is missing.

iPadOS 13.4 adds support for mouse input, though it is limited by the OS such that it doesn't work with games that capture the mouse pointer (like most FPS games) and you can't hold more than one mouse button down at a time. iPadOS 14 solves both of these limitations, however not all mice are compatible with the new enhanced iPadOS 14 mouse support. Compatibility for non-Apple mice seems to be best when connected via USB (with a USB-C to USB-A or Lightning to USB-A adapter) instead of Bluetooth.

You can use the Apple TV remote as a touchpad to move the mouse cursor and click.

To disconnect from your PC while streaming on iOS, swipe from the left edge of the screen. To disconnect on tvOS, double-tap the Menu button on your Apple TV Remote.

iCade gamepads (old iOS gamepads that fake a Bluetooth keyboard) are not supported by Moonlight.

## Adding custom programs that are not automatically found
You can stream any almost any game or app by adding the EXE file to GFE manually (if it's not found by the automatic app scan). Open GeForce/Quadro Experience, click the **Settings (gear) button**, click **SHIELD** on the sidebar, then click the **Add button** on the right. Browse to the app or file you want to add and click OK. You can rename the app using the **Edit button**.

The next time the client opens and displays the App List, the newly added programs and games should be displayed and ready to stream.

If quitting an application doesn't stop Moonlight, press *Ctrl+Shift+Alt+Q* on Moonlight PC to quit the streaming session. On Moonlight Android and iOS, pressing the home key will switch out of the streaming session. Choose the **Quit Session** option from the App List to fully quit the streaming session. 

## Using Moonlight to stream your entire desktop
Follow the steps above for adding a custom program, but for the path use: **C:\windows\system32\mstsc.exe**

You can rename the remote desktop entry using the Edit button. When you click this entry, you will see your full desktop where you can run whatever you want.

Even though the mstsc.exe executable is typically used for Microsoft Remote Desktop, this is only an indicator to GeForce/Quadro Experience that you want to stream your desktop. It does not actually launch mstsc.exe or use RDP to stream.

***
