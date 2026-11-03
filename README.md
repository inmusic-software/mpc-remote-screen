# MPC Remote Screen Viewer

Shows your MPC's screen on your computer and lets you operate it remotely.

## Installing

**macOS** – drag *MPC Remote Screen Viewer* onto the Applications folder.

**Linux** – unzip anywhere and run *MPC Remote Screen Viewer* (it needs a desktop with
X11 and the ALSA sound library, which most distributions already have). Use the zip that
matches your computer: x86_64 (Intel / AMD) or arm64.

**Windows** – unzip anywhere and run *MPC Remote Screen Viewer.exe*. If SmartScreen warns
that the app is unrecognised, choose **More info**, then **Run anyway**.

## Connecting

1. Make sure your computer can reach the MPC on the network (WiFi, Ethernet or USB).
2. Enter the MPC's address and password and click **Connect**. Click the arrow at the end of the
   address field to pick one of the MPCs you have connected to before.
3. The MPC's screen appears. Once connected, the toolbar shows just the MPC you are attached to.
   Click **Disconnect** when you are done.

If it will not connect, the message in the window says why: a wrong address, nothing listening,
a firewall, or a wrong password. On macOS, also check System Settings > Privacy & Security >
Local Network and allow the app.

## Using it

The toolbar buttons are available once you are connected:

- **Control** – send your mouse, touch and keyboard to the MPC. (Greyed out if that MPC does not
  allow remote control.) Click the picture to press, drag to swipe, and just type.
- **Scale** – switch between fitting the picture to the window and showing it at its actual size
  (scroll, or drag while Control is off, to move around it).
- **Full Screen** – fill your screen with the picture. Press **Esc** to leave.
- **Audio** – play the MPC's audio on your computer.
- **Screenshot** – saves the current screen as a PNG on your Desktop, named by date and time.
- **Record** – records the screen to a `.mov` video on your Desktop, with the MPC's audio if Audio
  is on. Click it again to stop.
- **Device Info** – shows information about the MPC, your connection to it and how well it is
  performing. Click the button at the top right of that window for more detailed performance graphs.
- **Settings** – choose the audio output device, and:
  - **Show mouse presses on screen** – marks where you press, handy for demos and recordings.
  - **Show port number** – adds a port field to the toolbar, for the rare MPC that needs one.
  - **Show connection information** – shows the frame rate, data rate and picture quality in the
    status bar.

Everything is saved and is as you left it the next time you start.

Handy keys: **F11** full screen, **F12** Control on or off, and **Cmd+,** (macOS) or **Ctrl+,**
(Windows and Linux) for Settings.

---

© 2026 inMusic Brands, Inc. All rights reserved.
This software is provided under license; see the End User License Agreement in
`License.rtf`.
