# Viewer application changelog

The viewer version is defined once, in [`src/AppVersion.h`](src/AppVersion.h); CMake reads it from
there. The wire protocol is versioned separately, see
[docs/PROTOCOL_CHANGELOG.md](../docs/PROTOCOL_CHANGELOG.md).

## 1.5.0

- The device information window closes when the connection stops or drops.
- While audio is playing, the right-hand end of the status bar shows a stereo level meter with a volume
  slider above it (drag, scroll, or double-click for full volume); the connection figures move left of
  it. The volume is remembered. Settings has a new "Show volume and level meter" checkbox, on by default.
- The first connection attempt after launch is retried before any error is shown. It often failed at
  once with "No route to host" (the system not yet letting the app onto the network) and succeeded on
  the retry a couple of seconds later, so the window flashed an error before connecting; it now says
  "Connecting" until a second attempt has also failed.
- The Settings window is drawn like the Device Information and About windows: a rounded grey panel on the
  dark window background.
- The device information window shows the level of the audio received (peak dB below full scale): a
  sparkline in the Audio section, and a graph in the side panel that splits the audio latency graph's
  space in two, with latency on the left and level on the right. The level graphs are coloured by level,
  green through yellow and orange to red for very hot signals, and the graph's figure is shown to one decimal place.

## 1.4.0

- The audio settings window is now called Settings, with an "Audio Output" section and a new "General"
  section of checkboxes, all remembered between runs. Cmd+, (macOS) or Ctrl+, (Windows) opens it, and on
  macOS the application menu has a "Settings..." item.
  - "Show mouse presses on screen": while remote control is on, a press shows a translucent white ring
    round the pointer that grows in and, on release, shrinks and fades out. Video recordings include it.
  - "Show connection information": the statistics in the status bar (the same as Show Statistics in the
    menu).
  - "Show port number" (off by default): while it is off the toolbar has no port field, for a simpler
    toolbar; the saved port is still used.
- While connected the toolbar shows only the host (the device you are attached to): the port and
  password fields are hidden, and come back on disconnecting (the port as the Settings window has it).
- The device information window is now much more informative:
  - It shows the screen size and rotation, whether the device accepts control (and which input) and can
    share audio, the frame rate limit you chose, and live figures, refreshed twice a second: frame rate,
    video data rate, quality level, round-trip time and, for audio, its format, output rate, buffer
    (latency), dropouts and latency trims. A sparkline sits beside each of the figures that change.
  - A button at its top right opens a side panel of graphs over the last two minutes (and closes it
    again): frame rate, video data rate, round-trip time, quality level and audio latency, with vertical
    ticks on the latency graph where audio dropped out (red) or its latency was trimmed (blue). The history
    is gathered whenever the viewer is connected, so a graph is already full when the panel is first opened.
  - The panel also has a small map of the screen that lights up where the picture has changed lately and
    fades out ("Screen updates"), and a map of where the pointer was sent: blue for moves, green for drags
    and pink for clicks, with a key.
  - The window is no longer modal: it stays open, refreshing, while you keep using the main window. Its
    toolbar button has a pale yellow rounded highlight while the window is open, and clicking the button
    again closes the window.
- A device that does not report its model (an older protocol without DeviceInfo) is now called "MPC" in
  the device information window and the recent hosts list, instead of using its server name.

## 1.3.0

- While not connected, the window's background is now a dark grey rounded panel (matching the toolbar)
  patterned with rows of black Akai Professional logos at 45 degrees. The pattern is drawn to a bitmap
  once per window size, so repainting stays cheap.
- The Scale button's setting is now remembered the moment it changes, like the audio and control
  settings (scaling is on by default), and double-clicking the button also sizes the window to show
  the picture at 100%, like Shift-click.
- Added a Scale button (a two-headed arrow in a rounded box) between the Control and Full Screen buttons.
  It lights up green while scaling is on: the picture is scaled to fit the window. With scaling off, the
  picture is shown at actual size (1:1); where it is larger than the window, the mouse wheel scrolls it and,
  while remote control is off, dragging pans it. Shift-clicking the button sizes the window to show the whole
  picture at 1:1, as far as the screen allows.
- Fixed the last picture from a lost connection flashing on and off while the viewer retries. The
  picture is now shown only while connected.
- Esc now always leaves full screen, even while remote control is on (it was being sent to the
  device instead).
- In full screen, moving the mouse into the top-left corner fades in a circled "x" button that
  leaves full screen; moving away fades it out again.
- Shift-clicking the Full Screen button also scales the picture to fit the screen; the previous
  scaling is restored when full screen ends.
- Clicking the picture while remote control is off now also pulses the red dot in the status bar: a ring
  grows from its edge and fades as it spreads, to draw attention to the message.
- The viewer remembers whether audio and remote control were on, and switches them back on the next time it
  connects, if the device offers them.
- Added a Device Info button (a question mark in a rounded box) to the right of the Full Screen button. It opens
  a window with a table of the device's model, serial number, firmware version and the remote screen protocol
  version it uses; anything the device does not report (an older device) shows as "unknown".
- The recent hosts list now shows the product model the device reports, and the viewer remembers the
  device's serial number and firmware version for each host.
- The audio settings' active output channels list now matches the rest of the UI: a very dark grey rounded panel with
  rounded grey check boxes with red ticks, instead of JUCE's blue-grey.

## 1.2.0

- Restyled pop-up menus and drop-down lists to match the toolbar (flat, rounded, grey, with a
  rounded highlight), including the recent hosts list, and the Audio Output settings window now
  uses the viewer's look too.
- Fixed the toolbar sometimes not coming back after leaving full screen. It now always reappears
  when the window stops being full screen, however that happened, and Esc / F11 always leave full
  screen while the toolbar is hidden. Entering full screen now shows "Press Esc (or F11) to exit
  full screen mode" for a few seconds.
- Clicking the picture while remote control is off now says so in the status bar, with a small
  red dot beside the text for a few seconds.
- Added a Record button (a video camera) beside the Screenshot button, and File > Start/Stop
  Recording. It records the screen to a QuickTime `.mov` on the Desktop (Motion JPEG, only changed
  frames stored), together with the device's audio if the Audio button is on. While recording the
  button has a slowly pulsing red background; press it again to stop. Recording also stops, and the
  file is finished, if the connection ends. The finished video opens automatically in the default
  player.

## 1.1.0

- Added a Full Screen button to the toolbar, beside the remote control button. It does the same as
  F11 and View > Full Screen.
- Added a License info window, opened from the About window, listing the EULA and the third-party
  licenses used by the viewer.

## 1.0.0

- Initial recorded version. Earlier history was not recorded.
