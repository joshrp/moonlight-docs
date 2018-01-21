In this guide: 
* [Quick Setup Instructions](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#quick-setup-instructions)
* [Streaming over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#streaming-over-the-internet)
* [Moonlight Client Setup Instructions](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#moonlight-client-setup-instructions)
* [Touchscreen Controls for Android or iOS](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#touchscreen-controls-for-android-or-iOS)
* [Using a gamepad connected to the PC instead of the streaming device](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-a-gamepad-connected-to-the-pc-instead-of-the-streaming-device)
* [Adding custom programs that are not automatically found](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found)
* [Using Moonlight to stream your entire desktop](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-moonlight-to-stream-your-entire-desktop)

***

**PC Requirements** 

* NVIDIA GeForce GTX 600+ series GPU (GT-series and AMD GPUs aren't supported by NVIDIA GameStream)
* NVIDIA GeForce Experience (GFE) 2.1.1 or higher
* 720p or higher display connected to the PC

## Quick Setup Instructions
1. On your gaming PC, install the GeForce Experience software from [geforce.com](http://www.geforce.com). The PC may need a reboot after installation to finish setup.

2. Start GeForce Experience and click on the **Settings "gear" button**. Then choose the **SHIELD** option. Make sure the GameStream switch is in the **"on" position (green)**. If the SHIELD tab is not present, see the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

  <p align="center">
     <img src="https://github.com/moonlight-stream/moonlight-docs/wiki/images/gfe-gamestream-enable-small.png"/>
  </p>

3. Start Moonlight and make sure your client is connected to the same network as your PC. In most cases, your gaming PC will show up automatically in the PC list after a few seconds. Click the entry in the PC list to start pairing.

    * If your PC *doesn't* appear automatically for some reason, click the plus button and add your PC using its local network IP address. To find your gaming PC's local network address:

         1. Click on the Start menu, type **cmd**, and press Enter/Return

         2. Type **ipconfig** and press Enter/Return

         3. Try typing the number after "IPv4 Address" into Moonlight's Add PC dialog. Try all of the listed addresses until one of them works. Addresses starting with **192.168** are typically the correct ones.

    * If none of the IP addresses work, first try the [firewall setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#firewall-setup) and if that fails, try the [general troubleshooting steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

4. On your PC, enter the PIN displayed in Moonlight and accept the pairing dialog. If you don't see a pairing dialog, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

5. Try streaming a game or app to make sure everything is working.
  * By default, GeForce Experience will reserve Player 1 for the Moonlight client's gamepad. If you want to use a gamepad connected directly to your gaming PC, follow [these steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-a-gamepad-connected-to-the-pc-instead-of-the-streaming-device).
  * If you want to stream in 4K resolution, you must check the "Allow experimental features" checkbox on the GeForce Experience settings page.
  * If you can't successfully stream at all, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

## Firewall setup

If you are not able to stream when connected to the same network as your gaming PC, you may need to add firewall rules to stream successfully. First, try disabling your firewall software (usually Windows Firewall or a firewall integrated into your anti-virus software) to confirm it's a firewall-related problem.

### Windows Firewall
GeForce Experience should create rules for Windows Firewall automatically, but in the event that they don't work, you can create the rules required for streaming by using the following steps:
1. Open a Command Prompt or PowerShell window as administrator
2. Run the following 2 commands:
* netsh advfirewall firewall add rule name="GameStream UDP" dir=in protocol=udp localport=5353,47998-48010 action=allow
* netsh advfirewall firewall add rule name="GameStream TCP" dir=in protocol=tcp localport=47984,47989,48010 action=allow
3. Ensure your PC now appears online in Moonlight

### Other firewall software
For other firewall products, you should follow their instructions to create exceptions for the following ports:
* **TCP** 47984, 47989, 48010
* **UDP** 5353, 47998, 47999, 48000, 48002, 48010

## Streaming over the Internet

### Port forwarding (recommended for most users)

The following ports must be forwarded through your router for streaming to work with the latest version of GeForce Experience:
* **TCP** 47984, 47989, 48010
* **UDP** 47998, 47999, 48000, 48002, 48010

**If your port forwarding setup just stopped working recently, check that TCP 48010 is forwarded. It is newly required with GeForce Experience v3.12.**

### IPv6 (certain ISPs only)

If you are lucky enough to have native IPv6 connectivity to your host PC and client device on the networks you'd like to stream on, you may opt to use IPv6 instead of port forwarding. This has the advantage of allowing you to stream from multiple PCs behind a single Internet connection, which is not possible with port forwarding. This option is only recommended for those very familiar with network administration. You may combine these steps with port forwarding above to stream over IPv4 or IPv6, depending on your client's connectivity.

1. Navigate to http://test-ipv6.com/ on both your host PC and client device and confirm they both score 10/10 on the networks you will be streaming from. You may need to disable Chrome's Data Compression option to get accurate results on mobile.

  * If your host PC doesn't score 10/10, you won't be able to use this method for streaming over the Internet with your ISP.

  * If your client device doesn't score 10/10 but your host PC does, you won't be able to stream over IPv6 on the current network but another network may work.

2. Install the [GameStream IPv6 Forwarder](https://github.com/moonlight-stream/GS-IPv6-Forwarder/releases) on your host PC.

3. Configure your router's IPv6 firewall (typically separate from the IPv4 firewall/port forwarding) to allow the ports listed in the section above.

4. In Moonlight, click Add PC and type the IPv6 address of your PC. Your PC should appear online (or remain online, if you already had IPv4 connectivity to it).

All officially supported Moonlight clients (iOS, Chrome, Android) support streaming from servers over IPv6. Unofficial clients (Embedded, Vita) may not.

### Having trouble?
* If you get an RTSP error or have no audio or video when streaming from outside your network, check that the UDP ports above are forwarded correctly. Make sure they are forwarded as UDP, not TCP in your router settings.

* If your PC doesn't appear online at all, check the TCP ports are correctly forwarded.

To find the external IPv4 address of your server, when connected to your network, use a service like http://whatip.me/ to determine the IPv4 address another computer uses to talk to you. _Ensure you always use your IPv4 address not your IPv6 address._

To stream over the Internet, in your client: If your PC already appears online when connecting over the Internet, you're all set. If it doesn't, tap on the add button in Moonlight, then enter in the IPv4 address (or hostname, if you set one up for your router). Your IPv4 address should look something like 123.123.123.123. If you see an address with semi-colons, that's an IPv6 address and won't work for Moonlight. If your PC still won't come online, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

_Note:_ Some Internet Service providers change the external IP address in use by any given subscriber on a regular basis. Since Moonlight needs to connect to the right IP address, this change can cause problems for Moonlight. Using a dynamic DNS service like [No-IP](http://www.noip.com) will give Moonlight a consistent name to use for connecting, even if the IP address that's associated with that name changes a lot. 

## Moonlight Client Setup Instructions
**Client Requirements**

* Android: An Android device running Android 4.1 (Jelly Bean) or newer. Newer and "flagship" devices with higher processor speeds are more likely to be able to handle Moonlight well by using the hardware video system on the device to produce smooth streaming without video stuttering or freezing.

* iOS: An iOS device running iOS 8.0 or later.

* PC (Chrome): Your PC should be new enough that it supports hardware-accelerated H.264 decoding, otherwise it will have to use CPU decoding. It must have the latest version of Google Chrome or Chromium installed. Chrome OS devices are supported.

* PC (Java): The Java client requires a fairly powerful CPU since it does video decoding on the CPU. You must also have Java 8 or higher installed.

**Internet and Network Requirements**

To have a good experience, you need a mid to high-end wireless router with a good wireless connection to your client device (5 Gigahertz (GHz) highly recommended, Wireless-N (802.11n) or better strongly recommended) and a good connection from your PC server to your router (Ethernet/wired connections highly recommended).

**Controls for Android devices**

For non-SHIELD devices and devices running Android 7.1 (Nougat) or earlier, using an external mouse with proper mouse capture on Android requires a rooted device. If you want to use an external mouse on your rooted device, you should download "Moonlight for Rooted Devices" on the Play Store or app-root-release.apk from releases. NVIDIA SHIELD devices and Android 8.0 (Oreo) have mouse capturing built-in that Moonlight uses without needing root. Moonlight for Rooted Devices is not available for Android 8.0, since the non-root version contains all features that required root using the new Android Oreo APIs.

To toggle capturing the mouse cursor on Moonlight for Rooted Devices, press Ctrl+Alt+Z.

**Mouse emulation**

If you don't have a mouse connected to your Android device, you can emulate one using a game controller. Press and hold the Start button to toggle mouse emulation. When mouse emulation is on, you can use either analog stick to move the cursor. The A button left clicks and the B button right clicks.

Most controllers will work just fine, but the following have been tested:
* Xbox 360 wired/wireless
* Xbox One wired (with Moonlight's built-in driver)
* PS3 wired (with Sixaxis Enabler app) or wireless (with SixAxis Controller app)
* PS4 wired via USB
* MOGA controller (see note below)
* Amazon Fire Game Controller
* Shield integrated controller

_MOGA controller users_:
If your controller has a switch with A and B, it must be switched to B to be used for streaming. If you have no switch, use the MOGA Universal Driver app.

_SixAxis controller users_:
Use SixAxis in "Native Gamepad" mode. The default button mapping needs to be adjusted to match the standard controller layout for streaming.

**Controls for iOS devices**

Apple devices only natively support MFi controllers. We recommend the "extended layout" controllers which have most buttons present on a typical Xbox 360 controller. Notably lacking are the L3 and R3 buttons and the select button. When using the Auto setting for on-screen controls, an overlay will be displayed containing the buttons that your physical controller is missing.

**Controls for PC clients**

PC clients support keyboard/mouse input and up to 4 game controllers. On Windows, XInput-compatible gamepads will be mapped automatically. On other systems, you may need to map the controller manually. 

To free the mouse cursor from the Moonlight window, press Ctrl+Alt+Shift. To quit streaming, press Ctrl+Alt+Shift+Q.

## Touchscreen Controls for Android or iOS

Moonlight for Android and iOS use the touch screen as a way of controlling the mouse cursor. Multi-touch devices can emulate more mouse functions than single-touch devices.

* Swiping across the screen moves the mouse cursor in the direction of the swipe.
* Tap once with one finger to left-click.
* Tap and hold in the same place to start a click and drag. After a short while, swipe the finger to drag in the direction of the swipe.
* Hold one finger down and tap a second finger to right-click.
* Tap with three fingers to open the on-screen keyboard (Android only for now). Only some keyboards work with Moonlight for Android - the [Hacker's Keyboard](https://play.google.com/store/apps/details?id=org.pocketworkstation.pckeyboard) seems to work well for everything but the arrow keys.

## Using a gamepad connected to the PC instead of the streaming device
Normally, Moonlight sends controller input from the streaming client which gets sent to the game by GFE. If you want to connect a controller to your PC instead of the streaming device, GFE can cause some problems because the emulated controller still appears to games as controller 1. Luckily there is a workaround for this. You'll need to rename the DLL that Nvidia is using to send controller input so it won't be used anymore. You may have to do the renaming again if GFE does an update, but it should allow you to use your controller normally on games that only support 1 controller.

* On GeForce Experience 3.0 and later, rename rxgamepadinput.dll to rxgamepadinput.dll.old in C:\Program Files\NVIDIA Corporation\NvStreamSrv and C:\Program Files (x86)\NVIDIA Corporation\NvStreamSrv.

* On older version of GeForce Experience (2.x), rename rxinput.dll to rxinput.dll.old in C:\Program Files\NVIDIA Corporation\NvStreamSrv and C:\Program Files (x86)\NVIDIA Corporation\NvStreamSrv.

## Adding custom programs that are not automatically found
You can stream any almost any game or app by adding the EXE file to GFE manually (if it's not found by the automatic app scan). Open GeForce Experience, click the **Settings (gear) button**, click **SHIELD** on the sidebar, then click the **Add button** on the right. Browse to the app or file you want to add and click OK. You can rename the app using the **Edit button**.

The next time the client opens and displays the App List, the newly added programs and games should be displayed and ready to stream.

If quitting an application doesn't stop Moonlight, press *Ctrl+Shift+Alt+Q* on Moonlight PC to quit the streaming session. On Moonlight Android and iOS, pressing the home key will switch out of the streaming session. Choose the **Quit Session** option from the App List to fully quit the streaming session. 

## Using Moonlight to stream your entire desktop
Follow the steps above for adding a custom program, but for the path use: **C:\windows\system32\mstsc.exe**

You can rename the remote desktop entry using the edit button. When you click this entry, you will see your full desktop where you can run whatever you want.

***
