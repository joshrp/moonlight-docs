In this guide: 
* [Prerequisites](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#prerequisites)
* [Quick Setup Instructions](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#quick-setup-instructions)
* [Touchscreen Controls for Android or iOS](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#touchscreen-controls-for-android-or-iOS)
* [Streaming over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#streaming-over-the-internet)
* [Using a gamepad connected to the PC instead of the streaming device](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-a-gamepad-connected-to-the-pc-instead-of-the-streaming-device)
* [Adding custom programs that are not automatically found](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found)
* [Using Moonlight to stream your entire desktop](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-moonlight-to-stream-your-entire-desktop)

***

##Prerequisites
**PC Requirements** 

* NVIDIA GeForce GTX 600/700/800/900 series or GTX 600M/700M/800M series GPU (GT-series GPUs won't work)
* NVIDIA GeForce Experience (GFE) 2.1.1 or higher

In addition, NVIDIA suggests the following for your PC server (http://www.geforce.com/geforce-experience/system-requirements)

* Operating System: Windows 7 or newer

* A CPU of reasonable newness (Intel Pentium G Series, Core 2 Duo, Quad Core i3, i5, i7, or an AMD Phenom II, Athlon II, Phenom X4, FX, or any newer, higher speed processor from either of those manufacturers)

* At least 2GB RAM, more preferred

* 20 MB of hard disk space for GeForce Experience, plus whatever additional hard disk space requirements are needed for the streamed game or game platform client, like Steam or Desura.

* A display that can handle at least 1280x720 (720p) resolution.

**Client Requirements**

* Android: An Android device running Android 4.1 (Jelly Bean) or newer. Newer and "flagship" devices with higher processor speeds are more likely to be able to handle Moonlight well by using the hardware video system on the device to produce smooth streaming without video stuttering or freezing.

* iOS: An iOS device running iOS 8.0 or later.

* PC: The PC client is currently in a beta status, and can't yet take advantage of the ability to process the video using the video card's hardware, so the client PC should have a relatively powerful CPU. Your client PC must have Java 8 installed.

**Internet and Network Requirements**

To have a good experience, you need a mid to high-end wireless router with a good wireless connection to your client device (5 Gigahertz (GHz) highly recommended, Wireless-N (802.11n) or better strongly recommended) and a good connection from your PC server to your router (Ethernet/wired connections highly recommended).

**Controls for Android devices**

Using an external mouse as a relative input on Android requires a rooted device. If you want to use an external mouse on your rooted device, you should download "Moonlight for Rooted Devices" on the Play Store or app-root-release.apk from releases.

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

##Quick Setup Instructions
1. On the server, download the GeForce Experience software from http://www.geforce.com/geforce-experience/download and install it. The server may need a reboot after installation to finish setup. Make sure GeForce Experience is open, updated, and that you've scanned for games. You should see the NVIDIA icon in your system tray. If you don't, try rebooting your machine or reinstalling GeForce Experience. Moonlight may not be able to pair if the NVIDIA icon isn't shown.

2. Start up GeForce Experience on the server and navigate to the **Preferences** tab. Then choose the **SHIELD** option. Make sure the **Allow this PC to stream games to SHIELD devices** checkbox is checked. To set up streaming from the Internet, see [Streaming over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#streaming-over-the-internet) later on in the guide.

3. Download, install, and start your client. In most cases, your PC server will show up automatically in the PC list. Click the entry in the PC list (PC: and then click on the **Pair** button) to start pairing. If not, click the plus button and add your PC using its local network IP address. If this doesn't work, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

    * Find the server's local network address

         1. Click on the Start menu and run the command prompt (cmd.exe)

         2. Type *ipconfig /all* and press Enter/Return

         3. A local network addresses usually takes the form of **192.168.x.yyy**

4. On your PC, enter the PIN displayed in Moonlight and accept the pairing dialog. If you don't see a pairing dialog, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

5. Choose your PC in the PC list and the app list will be displayed where you can select a game to stream.

##Touchscreen Controls for Android or iOS

Moonlight for Android and iOS use the touch screen as a way of controlling the mouse cursor. Multi-touch devices can emulate more mouse functions than single-touch devices.

* Swiping across the screen moves the mouse cursor in the direction of the swipe.
* Tap once with one finger to left-click.
* Tap and hold in the same place to start a click and drag. After a short while, swipe the finger to drag in the direction of the swipe.
* Hold one finger down and tap a second finger to right-click.
* Tap with three fingers to open the on-screen keyboard (Android only for now). Only some keyboards work with Moonlight for Android - the [Hacker's Keyboard](https://play.google.com/store/apps/details?id=org.pocketworkstation.pckeyboard) seems to work well for everything but the arrow keys.

##Streaming over the Internet

NVIDIA has disabled UPnP support in GFE 2.4.1, so it is necessary to forward ports manually if you're behind a router. Forwarding ports is only required to stream from outside your network. The following ports must be forwarded for streaming to work with the latest version of GeForce Experience:
* TCP 47984, 47989
* UDP 47998, 47999, 48000, 48010

If you are using an older version of GeForce Experience, you may need these additional ports:
* TCP 35043, 47995, 47996, 48010

To find the external IP address of your server, when connected to your network, use a service like http://www.whatismyip.com to determine the IP address another computer uses to talk to you.

_Note:_ Some Internet Service providers change the external IP address in use by any given subscriber on a regular basis. Since Moonlight needs to connect to the right IP address, this change can cause problems for Moonlight. Using a dynamic DNS service like [No-IP](http://www.noip.com) will give Moonlight a consistent name to use for connecting, even if the IP address that's associated with that name changes a lot. 

To stream over the Internet, in your client: If your PC already appears online when connecting over the Internet, you're all set. If it doesn't, tap on the add button in Moonlight, then enter in the IP address or name. If it still won't come online, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

##Using a gamepad connected to the PC instead of the streaming device
Normally, Moonlight sends controller input from the streaming client which gets sent to the game by GFE. If you want to connect a controller to your PC instead of the streaming device, GFE can cause some problems because the emulated controller still appears to games as controller 1. Luckily there is a workaround for this. You'll need to rename the DLL that Nvidia is using to send controller input so it won't be used anymore. On 32-bit and 64-bit Windows, rename rxinput.dll to rxinput.dll.old on in C:\Program Files\NVIDIA Corporation\NvStreamSrv. On 64-bit versions, there's another copy of the DLL in C:\Program Files (x86)\NVIDIA Corporation\NvStreamSrv which you'll want to rename. You may have to do the renaming again if GFE does an update, but it should allow you to use your controller normally on games that only support 1 controller.

##Adding custom programs that are not automatically found
You can stream any almost any game or app by adding the EXE file to GFE manually (if it's not found by the automatic app scan). Open GeForce Experience, click the **Preferences tab**, click **SHIELD** or **GameStream** on the sidebar, then click the add (+) button on the right. Browse to the app or file you want to add and click OK. You can rename the app using the edit button (pencil and paper) on the right (underneath the add button).

The next time the client opens and displays the App List, the newly added programs and games should be displayed and ready to stream.

If quitting an application doesn't stop Moonlight, press *Ctrl+Shift+Alt+Q* on Moonlight PC to quit the streaming session. On Moonlight Android and iOS, pressing the home key will switch out of the streaming session. Choose the **Quit Session** option from the App List to fully quit the streaming session. 

##Using Moonlight to stream your entire desktop
Follow the steps above for adding a custom program, but for the path use: **C:\windows\system32\mstsc.exe**

You can rename the remote desktop entry using the edit button. When you click this entry, you will see your full desktop where you can run whatever you want.

***

This page is under construction