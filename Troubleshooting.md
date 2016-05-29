Troubleshooting guide for Moonlight issues. Look at the troubleshooting steps for each of the following issues: 

* [Moonlight crashes](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#moonlight-crashes)
* [Can't pair or stream at all](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#cant-pair-or-stream-at-all)
* [No video displayed on device](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#no-video-displayed-on-device)
* [Video is choppy or laggy](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#video-is-choppy-or-laggy)
* [Apps crash when launched by Moonlight](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#apps-crash-when-launched-by-moonlight)
* [Bluetooth-related streaming issues](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#bluetooth-related-streaming-issues)
* [Nvidia stream is showing but game is not loading](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting#Nvidia-stream-is-showing-but-game-is-not-loading)

### Known application compatibility issues
* 3rd party firewalls (known issues with McAfee and Kaspersky)
* DisplayLink dock/display software
* TeamViewer
* KinoConsole Server
* Remote Desktop (streaming fails during and after an RDP session)

### Moonlight crashes
1. Please [send an email](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch) with details about the crash.

### Can't pair or stream at all
1. Reboot your PC and device.
2. Disable your PC's firewall.
3. Make sure a monitor is connected to your PC and turned on.
4. Make sure the NVIDIA Streaming Service is enabled and running.
5. Make sure the NVIDIA tray icon is visible. If it isn't, run "%ProgramFiles%\NVIDIA Corporation\Display\nvtray.exe"
6. Try removing some games from the search path of GeForce Experience. It can have issues with large game lists.
7. Check the list of known application compatibility issues above.
8. If all else fails: uninstall GeForce Experience, reboot, clean install GeForce Experience, and reboot again.

### No video displayed on device
1. Reboot your PC and device.
2. Lower Moonlight settings to 720p30
3. Check the list of known application compatibility issue above.
4. Disable your PC's firewall.
5. Uninstall GeForce drivers, reboot, clean install GeForce drivers, and reboot again.

### Video is choppy or laggy
1. Try streaming with Bluetooth disabled to see if your device has the Bluetooth issue detailed below.
2. Make sure your device is connected on 5 GHz and your PC is wired to your router.
3. Lower the bitrate slider.
4. Try using 720p30 which has the lowest requirements.

### Apps crash when launched by Moonlight
1. Uninstall GeForce drivers, reboot, clean install GeForce drivers, and reboot again.
2. Try launching them through Steam

### Bluetooth-related streaming issues
Depending on your phone/tablet, you may have a bad streaming experience if Bluetooth is active while streaming. This is a hardware issue due to the antenna wiring. If you experience this, you can try a USB Ethernet adapter or a controller that connects directly to your Android device via USB OTG.

### Nvidia stream is showing but game is not loading
MS eventlog will inform that SS2OSD.dll crashSS2OSD.dll crash failed. this is caused by the Asus Sound driver Sonicradar for adding effects to audio. 
1. Kill the process
2. Uninstall the software

Still having issues? Check out the [Get In Touch](https://github.com/moonlight-stream/moonlight-docs/wiki/Get-In-Touch) page.