_These troubleshooting checklists contain various suggestions to solve each potential issue. They are generally meant to be done in the order the steps are listed, however the list doesn't need to be fully completed if issue goes away during the process of troubleshooting._

Look at the troubleshooting steps for each of the following issues: 

* [Known application compatibility issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#known-application-compatibility-issues)
* [Moonlight crashes](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#moonlight-crashes)
* [Pairing dialog won't show up on PC](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#pairing-dialog-wont-show-up-on-pc)
* [SHIELD tab is missing in GeForce Experience](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#shield-tab-is-missing-in-geforce-experience)
* [Can't pair or stream at all](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#cant-pair-or-stream-at-all)
* [Games are missing from Moonlight](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#games-are-missing-from-moonlight)
* [No video displayed on device](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#no-video-displayed-on-device)
* [Video is choppy or laggy](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#video-is-choppy-or-laggy)
* [Apps crash or don't start when launched by Moonlight](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#apps-crash-or-dont-start-when-launched-by-moonlight)
* [Controller input doesn't work when streaming](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#controller-input-doesnt-work-when-streaming)
* [Bluetooth-related streaming issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#bluetooth-related-streaming-issues)

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

### Moonlight crashes
* Please [send an email](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch) with details about the crash.

### Pairing dialog won't show up on PC
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* Reboot your PC
* Delete the following registry value (if present): HKEY_LOCAL_MACHINE\SOFTWARE\NVIDIA Corporation\NvTray\ShowInSedona
* Open the NVIDIA Control Panel, select the "Desktop" menu at the top, and check "Show Notification Tray Icon".
* Uninstall GeForce Experience, reboot, clean install GeForce Experience, and reboot again.
* [Send us an email](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch)

### SHIELD tab is missing in GeForce Experience
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* Reboot your PC
* Install the latest GPU driver from NVIDIA's website
* Uninstall and reinstall GeForce Experience

### Can't pair or stream at all
* Make sure a monitor is connected to your PC and turned on, and you are logged in.
* Reboot your PC and client device.
* If you're trying to stream 4K, make sure the "Allow experimental features" checkbox in GeForce Experience settings is checked.
* Disable your PC's firewall and anti-virus, and reboot again.
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* If your PC is running Windows Server, install the qWave service.
* Make sure the NVIDIA Streaming Service is enabled and running.
* Uninstall GeForce Experience, reboot, clean install GeForce Experience, and reboot again.
* [Send us an email](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch)

### Games are missing from Moonlight
* If nothing appears at all (not even Steam), try restarting your PC. If that doesn't work, uninstall GeForce Experience, reboot your PC, then reinstall GeForce Experience again and scan for games.
* Make sure the folder where your games are installed is listed in GeForce Experience. Add it by opening GeForce Experience, clicking on the Preferences tab, then clicking the + button and navigating to the correct folder.
* You can add games manually that aren't detected as streamable by GeForce Experience [using this guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#adding-custom-programs-that-are-not-automatically-found)

### No video displayed on device
* Make sure a monitor is connected to your PC, turned on, and that you can see your desktop.
* Reboot your PC and device.
* Disable your PC's firewall and anti-virus, and reboot again.
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* Uninstall GeForce Experience, reboot, clean install GeForce Experience, and reboot again.
* [Send us an email](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch)

### Video is choppy or laggy
* Try streaming with Bluetooth disabled to see if your device has the Bluetooth issue detailed below.
* Make sure your device is connected on 5 GHz and your PC is wired to your router.
* Lower the bitrate slider.
* Try using 720p30 which has the lowest requirements.
* Try forcing your PC's Ethernet adapter to run at 100Mb Full Duplex in Device Manager.
* [Send us an email](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch)

### Apps crash or don't start when launched by Moonlight
* Check the list of known application compatibility issues above. Uninstall any programs on that list, and reboot.
* Try launching them through Steam.
* Uninstall GeForce drivers, reboot, clean install GeForce drivers, and reboot again.
* [Send us an email](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch)

### Controller input doesn't work when streaming
* Try a different game or Steam Big Picture
* If you're using a controller directly connected to your GeForce PC, you may need to follow an extra step to prevent the local controller from being overridden. Follow [the steps here](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-a-gamepad-connected-to-the-pc-instead-of-the-streaming-device).

### Bluetooth-related streaming issues
Depending on your phone/tablet, you may have a bad streaming experience if Bluetooth is active while streaming. This is a hardware issue due to the antenna wiring. If you experience this, you can [try this](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#using-a-gamepad-connected-to-the-pc-instead-of-the-streaming-device) as a workaround.

Still having issues? Check out the [Get In Touch](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch) page.