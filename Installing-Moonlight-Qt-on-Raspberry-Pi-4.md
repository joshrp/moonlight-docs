Beginning with Moonlight Qt v2.0.0, Raspberry Pi 4 support is in beta. As is typical with beta releases, the usual caveats apply: this may not perform well for you; it may crash/hang or just not work at all. Please [report bugs](https://github.com/moonlight-stream/moonlight-qt/issues) if you encounter issues.

[Moonlight Qt](https://github.com/moonlight-stream/moonlight-qt) differs from [Moonlight Embedded](https://github.com/irtimmer/moonlight-embedded) in that it provides a graphical user interface for Moonlight (even without X running), while Moonlight Embedded is command-line only. If you experience issues streaming to your Pi, trying the other client might resolve the problem. You can have both clients installed at the same time and switch between the two by running `moonlight` (Moonlight Embedded) or `moonlight-qt` (Moonlight Qt).

NOTE: If you installed an earlier preview version of Moonlight Qt prior to v2.0.0, you must switch to the official repository to receive the update to v2.0.0 and future updates. To do so, run the the commands listed in the installation section and then those listed in the updates section.

Requirements:
- Raspberry Pi 4 (earlier Raspberry Pi models may not perform well with the current beta)
- Raspbian Buster

## Installation
Run the following commands to install Moonlight Qt to your Raspberry Pi:
```
echo "deb https://dl.bintray.com/moonlight-stream/moonlight-raspbian buster main" | sudo tee /etc/apt/sources.list.d/moonlight-raspbian.list 
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
sudo apt update
sudo apt install moonlight-qt
```

You can then launch Moonlight from your Raspberry Pi's desktop or via the `moonlight-qt` command in the terminal.

## Common problems and solutions

### No audio output

The Raspberry Pi OS folks have [recently released an update](https://www.raspberrypi.org/blog/new-raspberry-pi-os-release-december-2020/) that switches from ALSA to PulseAudio for audio output. By default, Moonlight uses ALSA for audio output on the Raspberry Pi. This change to PulseAudio causes audio output to stop working, unless you configure Moonlight to use PulseAudio instead of ALSA.

To work around this problem, run Moonlight using the following command:
```
SDL_AUDIODRIVER=pulseaudio moonlight-qt
```

This will no longer be necessary in the next release of Moonlight Qt which will use PulseAudio by default.

### GUI not appearing when launched from the console
The GUI will appear on the monitor connected to the mini-HDMI port _closest to the USB-C power cable_. This is the primary display output port.

Make sure your monitor is connected to the correct port if you don't see the UI appear when you start Moonlight from outside the Raspberry Pi desktop environment.

### Decoder Errors with a 4K 60 Hz Monitor
If your Raspberry Pi is configured for 4K 60 Hz output, you will need to increase the amount of GPU memory for the hardware video decoder to work.

Run the following commands:
```
echo "gpu_mem=128" | sudo tee -a /boot/config.txt
sudo reboot
```

NOTE: The Raspberry Pi 4's H.264 decoder is still limited to 1080p. 4K streaming is only available using HEVC, which is not yet supported on the Raspberry Pi.

### Updates
To update Moonlight Qt after you've installed it, run:
```
sudo apt update
sudo apt upgrade
```