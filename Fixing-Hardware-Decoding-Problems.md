<a href="https://moonlight-stream.org/discord"><img src="https://moonlight-stream.org/images/discord.png" height="70" alt="Join our Discord"></a>

# Windows
Moonlight uses DXVA2 for hardware acceleration on Windows. All modern GPUs from AMD, NVIDIA, and Intel should support hardware decoding of H.264 via DXVA2 with the proper drivers installed.

If you have issues with hardware decoding:
* Ensure your client PC GPU drivers are properly installed and up-to-date from the GPU manufacturer or PC vendor's website.
* If your client PC supports NVIDIA Optimus, try switching Moonlight to run on the integrated Intel GPU.
* Ensure you're not using Remote Desktop to access your PC. This prevents your GPU from being usable for rendering.

# Mac
Moonlight uses VideoToolbox for hardware acceleration on macOS. All Macs capable of running the latest release of macOS should support hardware H.264 decoding without any work required.

If you are using Hackintosh machine, you'll need to find a GPU driver (if available) that correctly implements VideoToolbox decoding for H.264 video.

# Linux
Moonlight uses VAAPI, VDPAU, and NVDEC for hardware acceleration on Linux. One of those APIs should be compatible with any modern GPU. The most common issue preventing it from working properly is a missing driver package for your GPU.

* Hardware acceleration support may differ between included libraries within the Flatpak, Snap, and AppImage packages. If you have hardware acceleration issues, trying a different Moonlight package may resolve the issue.

* If you are running Moonlight via AppImage, you will need to ensure the appropriate video acceleration drivers are installed on your system. On Debian-based distros like Ubuntu, run `apt-get install va-driver-all vdpau-driver-all`. On newer Intel hardware, you may need to also run `apt install intel-media-va-driver-non-free`.

* If you installed Moonlight via Flatpak, run `flatpak update` to ensure the Flatpak runtime has installed the matching extension for your current GPU.

* If you are running Wayland on GNOME, you may need to launch Moonlight with the `-platform wayland` option to ensure hardware acceleration works.
    * If you installed Moonlight via Flatpak, you would run `flatpak run com.moonlight_stream.Moonlight -platform wayland`
    * The Snap package of Moonlight does not currently support hardware acceleration on Wayland.
    * Decoding performance under Wayland may not be as good as X11, so try X11 if you experience performance issues.

# Raspberry Pi
Moonlight uses the Raspberry Pi's H.264 hardware decoder using the MMAL decoder library. MMAL requires enough GPU memory to be allocated to store video frames.

If the H.264 decoder fails to initialize, this usually means that the amount of reserved GPU memory is insufficient.

To increase the reserved GPU memory, run the following commands:
```
echo "gpu_mem=128" | sudo tee -a /boot/config.txt
sudo reboot
```