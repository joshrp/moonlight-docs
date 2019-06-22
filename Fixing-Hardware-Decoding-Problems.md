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
Moonlight uses VAAPI and VDPAU for hardware acceleration on Linux. One of those two APIs should be compatible with any modern GPU. The most common issue preventing it from working properly is a missing VAAPI or VDPAU driver package for your GPU.

* If you installed Moonlight via Flatpak, run `flatpak update` to ensure the Flatpak runtime has installed the matching extension for your current GPU.

* If you are running Wayland on GNOME, you may need to launch Moonlight with the `-platform wayland` option to ensure hardware acceleration works.
    * If you installed Moonlight via Flatpak, you would run `flatpak run com.moonlight_stream.Moonlight -platform wayland`
    * The Snap package of Moonlight does not currently support hardware acceleration on Wayland.
    * Decoding performance under Wayland may not be as good as X11, so try X11 if you experience performance issues.