_These troubleshooting checklists contain various suggestions to solve each potential issue. They are generally meant to be done in the order the steps are listed, however the list doesn't need to be fully completed if issue goes away during the process of troubleshooting._

You can chat with Moonlight developers and other users to help you resolve streaming issues on our [Discord server](https://discord.gg/MySTSdq).

Look at the troubleshooting steps for each of the following issues: 

* [Unable to stream at all on the same network as the PC](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#unable-to-stream-at-all-on-the-same-network-as-the-pc)
* [Unable to stream at all over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#unable-to-stream-at-all-over-the-internet)
* [Video is choppy or laggy](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#video-is-choppy-or-laggy)
* [No video (black screen)](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#no-video-black-screen)
* [Missing mouse cursor](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#missing-mouse-cursor)
* [Known application compatibility issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#known-application-compatibility-issues)
* [Pairing dialog won't show up on PC](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#pairing-dialog-wont-show-up-on-pc)
* [SHIELD tab is missing in GeForce Experience](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#shield-tab-is-missing-in-geforce-experience)
* [Games are missing from Moonlight](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#games-are-missing-from-moonlight)
* [Controller input doesn't work when streaming](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#controller-input-doesnt-work-when-streaming)
* [Bluetooth-related streaming issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#bluetooth-related-streaming-issues)

### Unable to stream at all on the same network as the PC
* Ensure you've enabled GameStream in GeForce Experience per the [setup guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide)
* Reboot your PC and client device.
* If your gaming PC is connected to your home network via multiple connections (like both Ethernet and WiFi), disconnect all connections except for the fastest one (usually Ethernet).
* Check the list of [known application compatibility issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#known-application-compatibility-issues). Try uninstalling any programs on that list one to see if one of them is interfering.
* Make sure your primary monitor is connected to your NVIDIA GPU and turned on, and you are logged in.
* If you use a VPN for Internet access on your gaming PC, disable it to ensure your local network is accessible. You may also need to disable the setting to block local network access when the VPN is disconnected, if that option is available for your VPN software.
* Disable your PC's firewall and anti-virus, and reboot again. If this works, you can create a firewall exception using [the steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#firewall-setup).
* Uninstall GeForce Experience, reboot, clean install GeForce Experience, and reboot again.
* In an administrator command prompt, run `netsh winsock reset` and reboot your computer.
* If your PC is running Windows Server, install the qWave service and ensure the Windows Audio service is enabled and running.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Unable to stream at all over the Internet
* First, ensure you can stream successfully from your home network to ensure it's an issue specific to streaming over the Internet. If you can't, follow the instructions in the section above for general streaming issues.
* Make sure your gaming PC is running the [Moonlight Internet Streaming Helper](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) to automatically manage your port forwarding rules.
* Ensure UPnP is enabled in your router settings and delete any older Moonlight port forwarding entries.
* If you use a VPN for Internet access on your gaming PC, disable it to ensure your local network is accessible. You may also need to disable the setting to block local network access when the VPN is disconnected, if that option is available for your VPN software.
* Run the "Moonlight Internet Streaming Tester" found in the [Moonlight Internet Streaming Helper](https://github.com/moonlight-stream/Internet-Streaming-Helper/releases) and ask for help on our [Discord server](https://discord.gg/MySTSdq). Be sure to have the tester log handy.
* If the Moonlight Internet Streaming Tester says your ISP is running a [Carrier-grade NAT](https://en.wikipedia.org/wiki/Carrier-grade_NAT) that blocks hosting services like Moonlight, try these steps:
    * Ask your ISP for a public IP address. Many users have reported that their ISP is happy to provide one free of charge upon request.
    * Many users have reported good streaming performance using the [ZeroTier](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) setup steps.
    * You can try using the [IPv6 setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#ipv6-certain-isps-only) if your home ISP and client network both support IPv6. You can check this by seeing if you score a 10/10 on [this web IPv6 test](http://test-ipv6.com/).
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Video is choppy or laggy
* Try streaming with Bluetooth disabled to see if your device has the Bluetooth issue detailed below.
* Make sure your device is connected on 5 GHz and your PC is wired to your router.
* If you're streaming to a Mac over WiFi, try [disabling Location Services](https://github.com/moonlight-stream/moonlight-qt/issues/159#issuecomment-452675992).
* Lower the bitrate slider.
* Try using 720p30 which has the lowest requirements.
* Try forcing your PC's Ethernet adapter to run at 100Mb Full Duplex in Device Manager.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### No video (black screen)
* Ensure your monitor is powered on and connected to your NVIDIA GPU
* If you want to stream without a monitor connected, you can buy a cheap headless HDMI dongle like [this one](https://www.amazon.com/fit-Headless-GS-resolution-emulator-game-streaming/dp/B01EK05WTY)
* Try a different game or stream Steam to see if it's game-specific. You may be able to work around the game-specific issues by [streaming your whole desktop](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-moonlight-to-stream-your-entire-desktop) and starting the game from there.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Missing mouse cursor
* Ensure a mouse is connected to your host gaming PC
* If unable to physically connect a mouse, enable Mouse Keys on the host gaming PC to force Windows to display a mouse cursor.
    * If you just type "Mouse key" into the Start Menu search dialog, it should take you to the correct settings page.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Known application compatibility issues
Some installed applications and security products can interfere with GeForce Experience or GameStream. Depending on the configuration of these incompatible applications, you may or may not experience issues streaming.

Special-case issues:
* Parsec/Rainway/Steam In-Home Streaming
    * Disconnect your stream before using Moonlight to avoid encoder conflicts with other streaming apps
* NordVPN, TunnelBear, PIA, and other VPNs
    * Disable the VPN if Moonlight cannot discover your gaming PC or stream over the Internet
    * You may need to stop the VPN software from blocking local network access when it is disconnected
* Microsoft Remote Desktop
    * Streaming will fail until you log back in at the physical machine after connecting via RDP
    * Chrome Remote Desktop and TeamViewer can be used for remote access without breaking Moonlight

If you have one of the following, try disabling or uninstalling it:
* Some 3rd-party firewalls and anti-virus (Kaspersky, Panda, AVG, K9, ESET)
    * Kaspersky in particular may only [stop breaking Moonlight when it is fully uninstalled](https://www.reddit.com/r/theNvidiaShield/comments/4g5fft/gamestreaming_vs_kaspersky_resolved/).
* DisplayLink dock/display software
* Razer Synapse
* Razer Kraken software (APO Helper)
* ASUS SonicRadar
* ASUS KeyBot
* ASUS GameFirst

### Pairing dialog won't show up on PC
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* Reboot your PC
* Delete the following registry value (if present): HKEY_LOCAL_MACHINE\SOFTWARE\NVIDIA Corporation\NvTray\ShowInSedona
* Open the NVIDIA Control Panel, select the "Desktop" menu at the top, and check "Show Notification Tray Icon".
* Uninstall GeForce Experience, reboot, clean install GeForce Experience, and reboot again.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### SHIELD tab is missing in GeForce Experience
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* Reboot your PC
* Install the latest GPU driver from NVIDIA's website
* Uninstall and reinstall GeForce Experience

### Games are missing from Moonlight
* Make sure the folder where your games are installed is listed in GeForce Experience.
    * You can add a games folder by opening GeForce Experience, clicking on the Settings button, then clicking the + button and navigating to the correct folder.
* You can add games manually that aren't detected as streamable by GeForce Experience [using this guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found)

### Controller input doesn't work when streaming
* Ensure you're running GeForce Experience 3.15.0 or later
* In Steam Big Picture, go to Settings > Controller Settings, then uncheck all gamepad "Configuration Support" checkboxes
* Check if input works in Steam Big Picture to see if it's a game-specific compatibility issue
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Bluetooth-related streaming issues
Depending on your streaming device, you may have a bad experience if Bluetooth is active while streaming. This is a hardware limitation due to the antenna wiring. If you experience this and are streaming from within your home, you can try connecting the gamepad directly to your PC using a wireless adapter or Bluetooth.

Still having issues? Ask for help on our [Discord server](https://discord.gg/MySTSdq)