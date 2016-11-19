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

* NVIDIA GeForce GTX 600+ series GPU (GT-series and AMD GPUs aren't support by NVIDIA GameStream)
* NVIDIA GeForce Experience (GFE) 2.1.1 or higher

In addition, NVIDIA suggests the following for your PC server (http://www.geforce.com/geforce-experience/system-requirements)

* Operating System: Windows 7 or newer (Windows Server requires installing the qWave service)

* A CPU of reasonable newness (Intel Pentium G Series, Core 2 Duo, Quad Core i3, i5, i7, or an AMD Phenom II, Athlon II, Phenom X4, FX, or any newer, higher speed processor from either of those manufacturers)

* At least 2GB RAM, more preferred

* 20 MB of hard disk space for GeForce Experience, plus whatever additional hard disk space requirements are needed for the streamed game or game platform client, like Steam or Desura.

* A display that can handle at least 1280x720 (720p) resolution.

**Client Requirements**

* Android: An Android device running Android 4.1 (Jelly Bean) or newer. Newer and "flagship" devices with higher processor speeds are more likely to be able to handle Moonlight well by using the hardware video system on the device to produce smooth streaming without video stuttering or freezing.

* iOS: An iOS device running iOS 8.0 or later.

* PC (Chrome): Your PC should be new enough that it supports hardware-accelerated H.264 decoding, otherwise it will have to use CPU decoding. It must have the latest version of Google Chrome or Chromium installed. Chrome OS devices are supported.

* PC (Java): The Java client requires a fairly powerful CPU since it does video decoding on the CPU. You must also have Java 8 or higher installed.

**Internet and Network Requirements**

To have a good experience, you need a mid to high-end wireless router with a good wireless connection to your client device (5 Gigahertz (GHz) highly recommended, Wireless-N (802.11n) or better strongly recommended) and a good connection from your PC server to your router (Ethernet/wired connections highly recommended).

**Controls for Android devices**

For non-SHIELD devices, using an external mouse with proper mouse capture on Android requires a rooted device. If you want to use an external mouse on your rooted device, you should download "Moonlight for Rooted Devices" on the Play Store or app-root-release.apk from releases. NVIDIA SHIELD devices has mouse capturing built-in that Moonlight uses without needing root.

To toggle capturing the mouse cursor, press Ctrl+Alt+Z.

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

##Quick Setup Instructions
1. On the server, download the GeForce Experience software from http://www.geforce.com/geforce-experience/download and install it. The server may need a reboot after installation to finish setup. Make sure GeForce Experience is open, updated, and that you've scanned for games. You should see the NVIDIA icon in your system tray. If you don't, try rebooting your machine or reinstalling GeForce Experience. Moonlight may not be able to pair if the NVIDIA icon isn't shown.

2. Start up GeForce Experience on the server and click on the **Settings "gear" button**. Then choose the **SHIELD** option. Make sure the GameStream switch is in the **"on" position (green)**. If the SHIELD tab is not present, you may need to reinstall GeForce Experience. If that doesn't help, the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting). To set up streaming from the Internet, see [Streaming over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#streaming-over-the-internet) later on in the guide.

3. Download, install, and start your client. In most cases, your PC server will show up automatically in the PC list. Click the entry in the PC list (PC: and then click on the **Pair** button) to start pairing. If not, click the plus button and add your PC using its local network IP address. If this doesn't work, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

    * Find the server's local network address

         1. Click on the Start menu and run the command prompt (cmd.exe)

         2. Type *ipconfig /all* and press Enter/Return

         3. A local network addresses usually takes the form of **192.168.x.yyy**

4. On your PC, enter the PIN displayed in Moonlight and accept the pairing dialog. If you don't see a pairing dialog, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

5. Try streaming a game or app to make sure everything is working. If you can't successfully stream, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

##Touchscreen Controls for Android or iOS

Moonlight for Android and iOS use the touch screen as a way of controlling the mouse cursor. Multi-touch devices can emulate more mouse functions than single-touch devices.

* Swiping across the screen moves the mouse cursor in the direction of the swipe.
* Tap once with one finger to left-click.
* Tap and hold in the same place to start a click and drag. After a short while, swipe the finger to drag in the direction of the swipe.
* Hold one finger down and tap a second finger to right-click.
* Tap with three fingers to open the on-screen keyboard (Android only for now). Only some keyboards work with Moonlight for Android - the [Hacker's Keyboard](https://play.google.com/store/apps/details?id=org.pocketworkstation.pckeyboard) seems to work well for everything but the arrow keys.

##Streaming over the Internet

The following ports must be forwarded through your router for streaming to work with the latest version of GeForce Experience:
* TCP 47984, 47989
* UDP 47998, 47999, 48000, 48010

If you are using an older version of GeForce Experience, you may need these additional ports:
* TCP 35043, 47995, 47996, 48010

To find the external IP address of your server, when connected to your network, use a service like http://www.whatismyip.com to determine the IP address another computer uses to talk to you.

_Note:_ Some Internet Service providers change the external IP address in use by any given subscriber on a regular basis. Since Moonlight needs to connect to the right IP address, this change can cause problems for Moonlight. Using a dynamic DNS service like [No-IP](http://www.noip.com) will give Moonlight a consistent name to use for connecting, even if the IP address that's associated with that name changes a lot. 

To stream over the Internet, in your client: If your PC already appears online when connecting over the Internet, you're all set. If it doesn't, tap on the add button in Moonlight, then enter in the IP address or name. If it still won't come online, try the [troubleshooting steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

##Using a gamepad connected to the PC instead of the streaming device
Normally, Moonlight sends controller input from the streaming client which gets sent to the game by GFE. If you want to connect a controller to your PC instead of the streaming device, GFE can cause some problems because the emulated controller still appears to games as controller 1. Luckily there is a workaround for this. You'll need to rename the DLL that Nvidia is using to send controller input so it won't be used anymore. You may have to do the renaming again if GFE does an update, but it should allow you to use your controller normally on games that only support 1 controller.

* On GeForce Experience 3.0 and later, rename rxgamepadinput.dll to rxgamepadinput.dll.old in C:\Program Files\NVIDIA Corporation\NvStreamSrv and C:\Program Files (x86)\NVIDIA Corporation\NvStreamSrv.

* On older version of GeForce Experience (2.x), rename rxinput.dll to rxinput.dll.old in C:\Program Files\NVIDIA Corporation\NvStreamSrv and C:\Program Files (x86)\NVIDIA Corporation\NvStreamSrv.

##Adding custom programs that are not automatically found
You can stream any almost any game or app by adding the EXE file to GFE manually (if it's not found by the automatic app scan). Open GeForce Experience, click the **Settings (gear) button**, click **SHIELD** on the sidebar, then click the **Add button** on the right. Browse to the app or file you want to add and click OK. You can rename the app using the **Edit button**.

The next time the client opens and displays the App List, the newly added programs and games should be displayed and ready to stream.

If quitting an application doesn't stop Moonlight, press *Ctrl+Shift+Alt+Q* on Moonlight PC to quit the streaming session. On Moonlight Android and iOS, pressing the home key will switch out of the streaming session. Choose the **Quit Session** option from the App List to fully quit the streaming session. 

##Using Moonlight to stream your entire desktop
Follow the steps above for adding a custom program, but for the path use: **C:\windows\system32\mstsc.exe**

You can rename the remote desktop entry using the edit button. When you click this entry, you will see your full desktop where you can run whatever you want.

***

This page is under construction