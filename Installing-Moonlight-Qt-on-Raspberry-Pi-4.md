NOTE: If you installed an earlier preview version of Moonlight Qt prior to v2.0.0, you must switch to the official repository to receive the update to v2.0.0 and future updates. To do so, run the the commands listed in the installation section and then those listed in the updates section.

Requirements:
- Raspberry Pi 4 (earlier Raspberry Pi models may not perform well)
- Raspbian Buster or Bullseye (**see special Bullseye instructions below**)

[![Hosted By: Cloudsmith](https://img.shields.io/badge/OSS%20hosting%20by-cloudsmith-blue?logo=cloudsmith&style=for-the-badge)](https://cloudsmith.com)

## Installation
Run the following commands to install Moonlight Qt to your Raspberry Pi:
```
curl -1sLf 'https://dl.cloudsmith.io/public/moonlight-game-streaming/moonlight-qt/setup.deb.sh' | distro=raspbian codename=buster sudo -E bash
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

### Raspbian Bullseye
The newest Raspberry Pi OS (Bullseye) defaults to a display driver that doesn't support Moonlight's low-latency H.264 decoder.

To fix this, you can edit the `/boot/config.txt` file:
1. Run `sudo nano /boot/config.txt`
2. Scroll down using the arrow keys until you see the line that says `dtoverlay=vc4-kms-v3d`
3. Change that line to `dtoverlay=vc4-fkms-v3d`
4. Press Ctrl+X, press Y, then press Enter
5. Reboot your Pi

**Workarounds for incompatible software (Kodi v19+)**

If you are using software that requires `vc4-kms-v3d` (such as Kodi v19 or later), you can force Moonlight to use the slower V4L2M2M decoder to enable it to function in this scenario. V4L2M2M adds between 1 and 2 frames of additional latency at 1080p compared to the optimal solution above (using `vc4-fkms-v3d`).

To enable the V4L2M2M decoder, launch Moonlight with the following command: `H264_DECODER_HINT=h264_v4l2m2m DRM_FORCE_DIRECT=1 moonlight-qt`

It is _highly_ recommended that you enable the HEVC decoder (see "HEVC support" above) to avoid the performance cost of V4L2M2M for host PCs that support HEVC encoding (GTX 900 series and newer).

## Common problems and solutions

### Video decoder error dialog when starting Moonlight or black screen when streaming
This is most likely because you're running Raspbian Bullseye or another Linux distro that enables the Full KMS display driver by default.

To fix this, you can follow the steps above in the Raspbian Bullseye section.

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