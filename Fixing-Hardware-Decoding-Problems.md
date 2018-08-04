# Windows
Moonlight uses DXVA2 for hardware acceleration on Windows. All modern GPUs from AMD, NVIDIA, and Intel should support hardware decoding of H.264 via DXVA2 with the proper drivers installed.

If you have issues with hardware decoding:
* Ensure your GPU drivers are properly installed from the GPU manufacturer or PC vendor's website.
* Ensure you're not using Remote Desktop to access your PC. This prevents your GPU from being usable for rendering.

# Mac
Moonlight uses VideoToolbox for hardware acceleration on macOS. All Macs capable of running the latest release of macOS should support hardware H.264 decoding without any work required.

If you are using Hackintosh machine, you'll need to find a GPU driver (if available) that correctly implements VideoToolbox decoding for H.264 video.

# Linux
Moonlight uses VAAPI and VDPAU for hardware acceleration on Linux. One of those two APIs should be compatible with any modern GPU. The most common issue preventing it from working properly is a missing VAAPI or VDPAU driver package for your GPU.

* Ensure your desktop session is running using X, not Wayland. On GNOME-based distros, you can switch this at the logon screen by clicking the little gear icon.

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