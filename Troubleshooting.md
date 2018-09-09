_These troubleshooting checklists contain various suggestions to solve each potential issue. They are generally meant to be done in the order the steps are listed, however the list doesn't need to be fully completed if issue goes away during the process of troubleshooting._

You can chat with Moonlight developers and other users to help you resolve streaming issues on our [Discord server](https://discord.gg/MySTSdq).

Look at the troubleshooting steps for each of the following issues: 

* [Unable to stream at all on the same network as the PC](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#unable-to-stream-at-all-on-the-same-network-as-the-pc)
* [Unable to stream at all over the Internet](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#unable-to-stream-at-all-over-the-internet)
* [Video is choppy or laggy](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#video-is-choppy-or-laggy)
* [Known application compatibility issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#known-application-compatibility-issues)
* [Pairing dialog won't show up on PC](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#pairing-dialog-wont-show-up-on-pc)
* [SHIELD tab is missing in GeForce Experience](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#shield-tab-is-missing-in-geforce-experience)
* [Games are missing from Moonlight](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#games-are-missing-from-moonlight)
* [Controller input doesn't work when streaming](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#controller-input-doesnt-work-when-streaming)
* [Bluetooth-related streaming issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#bluetooth-related-streaming-issues)

### Unable to stream at all on the same network as the PC
* Ensure you've enabled GameStream in GeForce Experience
* Make sure your primary monitor is connected to your NVIDIA GPU and turned on, and you are logged in.
* Reboot your PC and client device.
* Disable your PC's firewall and anti-virus, and reboot again. If this works, you can create a firewall exception using [the steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#firewall-setup).
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* If your PC is running Windows Server, install the qWave service.
* Uninstall GeForce Experience, reboot, clean install GeForce Experience, and reboot again.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Unable to stream at all over the Internet
* First, ensure you can stream successfully from your home network to ensure it's an issue specific to streaming over the Internet. If you can't, follow the instructions in the section above for general streaming issues.
* Ensure you've forwarded the required ports [here](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#streaming-over-the-internet). **TCP 48010 is now required with the GeForce Experience v3.12 update.**
* On your home network, go to http://canyouseeme.org/ and check port 47989 and 47984 using the tool to ensure they are both open. If they are not, your port forwarding is not configured correctly (or you have another issue, possibly listed below).
* On your home network, go to https://whatsmyip.com/ to get your current external IP address. Use the Add PC button and type that address to ensure Moonlight has your router's current IP address (which can change periodically depending on your ISP). If your IP address changes frequently, you may look at a Dynamic DNS provider such as https://www.noip.com/ to allow you to use a hostname instead.
* Make sure your PC's internal IP address (that you forwarded to) hasn't changed since you created the forwarding rules. If so, you may assign a static IP reservation to it via your router or a static IP address on the PC itself to prevent it from changing. Update the forwarding rules to point to the new IP address.
* Double-check that you forwarded the UDP ports as UDP and not TCP (especially if you get no audio or video)
* Ensure you don't have 2 or more devices acting as routers in your network (for example, an ISP modem/router combo and your own router). This is known as a double-NAT and can be solved by switching one of them to bridged or AP mode (if supported by the hardware). Double-NAT interferes with all applications that rely on UPnP or port forwarding.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Video is choppy or laggy
* Try streaming with Bluetooth disabled to see if your device has the Bluetooth issue detailed below.
* Make sure your device is connected on 5 GHz and your PC is wired to your router.
* Lower the bitrate slider.
* Try using 720p30 which has the lowest requirements.
* Try forcing your PC's Ethernet adapter to run at 100Mb Full Duplex in Device Manager.
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Known application compatibility issues
* Some 3rd-party firewalls and anti-virus (Kaspersky, Panda, AVG, K9, ESET)
* DisplayLink dock/display software
* Razer Synapse
* Razer Kraken software (APO Helper)
* TeamViewer
* KinoConsole Server
* ASUS SonicRadar
* ASUS KeyBot
* ASUS GameFirst
* Microsoft Remote Desktop (streaming fails during and after an RDP session)

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
* Make sure the folder where your games are installed is listed in GeForce Experience. Add it by opening GeForce Experience, clicking on the Preferences tab, then clicking the + button and navigating to the correct folder.
* You can add games manually that aren't detected as streamable by GeForce Experience [using this guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found)

### Controller input doesn't work when streaming
* Try a different game or Steam Big Picture
* If you're using a controller directly connected to your GeForce PC, you may need to follow an extra step to prevent the local controller from being overridden. Follow [the steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-a-gamepad-connected-to-the-pc-instead-of-the-streaming-device).
* Ask for help on our [Discord server](https://discord.gg/MySTSdq)

### Bluetooth-related streaming issues
Depending on your phone/tablet, you may have a bad streaming experience if Bluetooth is active while streaming. This is a hardware issue due to the antenna wiring. If you experience this, you can [try this](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-a-gamepad-connected-to-the-pc-instead-of-the-streaming-device) as a workaround.

Still having issues? Ask for help on our [Discord server](https://discord.gg/MySTSdq)