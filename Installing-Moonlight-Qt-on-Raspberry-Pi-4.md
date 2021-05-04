Beginning with Moonlight Qt v2.0.0, Raspberry Pi 4 support is in beta. As is typical with beta releases, the usual caveats apply: this may not perform well for you; it may crash/hang or just not work at all. Please [report bugs](https://github.com/moonlight-stream/moonlight-qt/issues) if you encounter issues.

[Moonlight Qt](https://github.com/moonlight-stream/moonlight-qt) differs from [Moonlight Embedded](https://github.com/irtimmer/moonlight-embedded) in that it provides a graphical user interface for Moonlight (even without X running), while Moonlight Embedded is command-line only. If you experience issues streaming to your Pi, trying the other client might resolve the problem. You can have both clients installed at the same time and switch between the two by running `moonlight` (Moonlight Embedded) or `moonlight-qt` (Moonlight Qt).

NOTE: If you installed an earlier preview version of Moonlight Qt prior to v2.0.0, you must switch to the official repository to receive the update to v2.0.0 and future updates. To do so, run the the commands listed in the installation section and then those listed in the updates section.

Requirements:
- Raspberry Pi 4 (earlier Raspberry Pi models may not perform well with the current beta)
- Raspbian Buster

[![Hosted By: Cloudsmith](https://img.shields.io/badge/OSS%20hosting%20by-cloudsmith-blue?logo=cloudsmith&style=for-the-badge)](https://cloudsmith.com)

## Installation
Run the following commands to install Moonlight Qt to your Raspberry Pi:
```
curl -1sLf 'https://dl.cloudsmith.io/public/moonlight-game-streaming/moonlight-qt/setup.deb.sh' | sudo -E bash
sudo apt install moonlight-qt
```

You can then launch Moonlight from your Raspberry Pi's desktop or via the `moonlight-qt` command in the terminal.

### Updates
To update Moonlight Qt after you've installed it, run:
```
sudo apt update
sudo apt upgrade
```

### HEVC support
Beginning with Moonlight Qt v3.1.2, the Raspberry Pi 4 builds have experimental support for streaming HEVC video using hardware decoding.

To enable HEVC support:
- Add `dtoverlay=rpivid-v4l2` to your `/boot/config.txt` and reboot your Pi.
- You must run Moonlight directly from the console for HEVC support to be enabled. If you have your Pi set to boot to GUI, you can press Ctrl+Alt+F1 to switch to TTY 1 and run moonlight-qt from there.

## Common problems and solutions

### No audio output or crackly audio output

The Raspberry Pi OS team has [recently released an update](https://www.raspberrypi.org/blog/new-raspberry-pi-os-release-december-2020/) that switches from ALSA to PulseAudio for audio output. In response, Moonlight Qt v3.0.0 now defaults to using PulseAudio on the Raspberry Pi.

If you're running Raspberry Pi OS and experiencing audio problems with Moonlight, you should run the following commands to upgrade your OS with support for PulseAudio:
```
sudo apt update
sudo apt upgrade
sudo reboot
```

For older distros that still use ALSA, you may find that audio doesn't work correctly with Moonlight Qt v3.0.0 or later. If that's the case, you can tell Moonlight to use ALSA by running with:
```
PULSE_SERVER=none moonlight-qt
```

### GUI not appearing when launched from the console
The GUI will appear on the monitor connected to the mini-HDMI port _closest to the USB-C power cable_. This is the primary display output port.

Make sure your monitor is connected to the correct port if you don't see the UI appear when you start Moonlight from outside the Raspberry Pi desktop environment.

If your monitor is plugged into the primary HDMI output and you still don't see the UI when you start Moonlight from the console, try starting Moonlight with the following command:
```
QT_QPA_EGLFS_ALWAYS_SET_MODE=1 moonlight-qt
```

### Decoder Errors with a 4K 60 Hz Monitor
If your Raspberry Pi is configured for 4K 60 Hz output, you will need to increase the amount of GPU memory for the hardware video decoder to work.

Run the following commands:
```
echo "gpu_mem=128" | sudo tee -a /boot/config.txt
sudo reboot
```

NOTE: The Raspberry Pi 4's H.264 decoder is still limited to 1080p. 4K streaming is only available using HEVC, which is not yet supported on the Raspberry Pi.