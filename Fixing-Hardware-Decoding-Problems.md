# Windows
Moonlight uses DXVA2 for hardware acceleration on Windows. All modern GPUs from AMD, NVIDIA, and Intel should support hardware decoding of H.264 via DXVA2 with the proper drivers installed.

If you have issues with hardware decoding:
* Ensure your GPU drivers are properly installed and up-to-date from the GPU manufacturer or PC vendor's website.
* Ensure you're not using Remote Desktop to access your PC. This prevents your GPU from being usable for rendering.

# Mac
Moonlight uses VideoToolbox for hardware acceleration on macOS. All Macs capable of running the latest release of macOS should support hardware H.264 decoding without any work required.

If you are using Hackintosh machine, you'll need to find a GPU driver (if available) that correctly implements VideoToolbox decoding for H.264 video.

# Linux
Moonlight uses VAAPI and VDPAU for hardware acceleration on Linux. One of those two APIs should be compatible with any modern GPU. The most common issue preventing it from working properly is a missing VAAPI or VDPAU driver package for your GPU.

* Run `flatpak update` to ensure the Flatpak runtime has installed the matching extension for your current GPU.

* Ensure your desktop session is running using X, not Wayland. On GNOME-based distros, you can switch this at the logon screen by clicking the little gear icon.

    * The following software limitations prevent hardware acceleration from being usable on Wayland:

        * VDPAU - the API has no Wayland rendering support at all
        * VAAPI - [missing DRI3 support](https://github.com/intel/libva/issues/79) that is required to render on XWayland
        * GNOME's Wayland compositor (Mutter) - [missing YUV surface support](https://github.com/intel/intel-vaapi-driver/issues/357) that is required for native Wayland rendering 

### Ubuntu

All GPUs:
1. `sudo apt install ubuntu-restricted-addons`
2. `sudo apt install va-driver-all vdpau-driver-all`

### Fedora

Intel GPUs:
1. `sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm`
2. `sudo dnf install intel-vaapi-driver`

Other GPUs:
1. `sudo dnf install mesa-vdpau-drivers`