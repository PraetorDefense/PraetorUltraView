# PraetorUltraView
UltraView is a high-performance, cross-platform thermal camera application built for FLIR Lepton and compatible USB/UVC thermal sensors. It provides advanced real-time image enhancement, measurement overlays, sensor calibration tools, and a modern UI in a single Python file.

Quick Start
1. Requirements

    Python 3.8+

    PyQt6

    OpenCV

    numpy

    pyusb (for raw Lepton support)

Install dependencies:

pip install pyqt6 opencv-python numpy pyusb

    Note:

        For Windows, all dependencies install via pip.

        For Linux, you may need to install libusb-1.0-0 via your package manager:
        sudo apt-get install libusb-1.0-0

2. USB Permissions (Linux only)

Create a udev rule for Lepton:

sudo nano /etc/udev/rules.d/99-lepton.rules

Paste:

SUBSYSTEM=="usb", ATTRS{idVendor}=="1e4e", ATTRS{idProduct}=="0100", MODE="0666"

Then reload:

sudo udevadm control --reload-rules && sudo udevadm trigger

Unplug/replug the camera.
3. Run UltraView

python UltraView.py

    On first launch, select your sensor from the list.

    The main window opens with live view and all controls.

Features
Sensor Support

    FLIR Lepton (PureThermal/USB): Via PyUSB

    UVC Cameras: Most thermal UVC webcams

Image Processing

    Color Palettes: Jet, White Hot, Black Hot, Rainbow, Grayscale, Viridis, Lava

    Super-Resolution: Experimental upscaling (2x–4x)

    Noise Reduction: Adjustable Gaussian denoise

    Bad/Hot Pixel Correction: Auto-detect and correct

Calibration & Measurement

    Calibration Wizard: Flat-Field Correction (FFC) and Offset tuning

    Spot Meter: Add unlimited spot temperature markers

    ROI Tool: Draw regions for max/min/average temperature

    Crosshair Overlay: Toggleable, for aiming

Capture & Recording

    Screenshot: Save current frame as PNG/JPG

    Video Recording: Save video at native FPS (MP4/AVI)

    Recent Files: Quick access (planned)

UI/UX

    UI Toggle: Hide all controls with Ctrl+H for fullscreen, unobstructed viewing

    Toolbar Shortcuts: Quick access to key features

    Resizable/Fit to View: Flexible layout for any screen

Usage Tips

    Toggle UI: Press Ctrl+H to hide or show toolbars and overlays.

    Calibration: Use the Calibration Wizard to improve measurement accuracy.

    Bad Pixels: Use “Auto-Detect Bad Pixels” when viewing a uniform scene for best correction.

    Video Recording: Recording uses the currently visible frame; change color palettes or overlays mid-recording for dynamic output.

Troubleshooting

    No Camera Detected:

        Ensure USB permissions (see above for Linux).

        Try another USB port.

        For UVC, test with a generic webcam to check OpenCV install.

    Frame Rate Slow:

        On laptops, ensure you’re using the correct USB port (avoid hubs).

        Try disabling Super-Resolution and denoise for higher FPS.

    PyUSB Errors:

        Run as sudo or fix udev rules.

        Windows users: PyUSB should work out-of-the-box.

    Black Screen:

        Sensor may be busy with another app—close other viewers (including GroupGets apps or Arduino tools).

    Settings Not Saving:

        Make sure Python can write to your home directory (check file permissions).

Developer Notes

    UltraView.py is fully self-contained.

    Extend/Modify: All major UI and processing classes are at the top level for easy hacking.

    Contributions: PRs and feature requests are welcome—just fork and submit!
