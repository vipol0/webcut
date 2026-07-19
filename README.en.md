# WEBCUT

A video editor that runs entirely in the browser — no install, no files uploaded to a server. Every operation (trimming, cropping, volume adjustment, rendering) happens right on the user's device.

🌐 [Русская версия](README.ru.md)

## Features

- **Import** — drag and drop a file or pick one from a dialog. Any format your browser can play works (MP4, WebM, MOV, OGV, etc.).
- **Trim by time** — pick the start and end of the clip right on the timeline, with a precise timecode.
- **Crop** — a crop frame right on top of the video, resizable and movable with mouse or touch.
- **Volume** — adjust the audio level with instant preview, baked into the final file.
- **Export**:
  - **Video** — MP4, MOV, or WebM (the available formats depend on the browser), with adjustable bitrate.
  - **Audio** — MP3 with a choice of bitrate (128 / 192 / 320 kbps).
  - **GIF** — animation with a choice of frame rate (5–15 fps).
- **Resolution** — ready-made presets 1080p / 720p / 480p / 360p (calculated from the current crop frame) or a custom width and height.
- **Video speed** — speed up the resulting clip from 1× to 4×.
- **Size comparison** — after export, the original and new file size are shown along with the difference.
- **Localization** — the interface is available in Russian and English, switchable with a button in the header; the choice is remembered.

## How it works

The file is opened locally right in the browser and never sent anywhere. Video frames are redrawn onto a `<canvas>`, taking cropping and the selected resolution into account, and the result is recorded using built-in browser APIs (`MediaRecorder`, `Web Audio API`) — the browser itself acts as the encoder.

Limitations: the available output formats and processing speed depend on the specific browser — this works best in Chrome and Edge.

## Tech stack

- Vanilla HTML / CSS / JavaScript, no build step or dependencies during development.
- [`lame.min.js`](libs/lame.min.js) — MP3 encoding.
- [`gifenc`](libs/gifenc.esm.js) — GIF animation encoding.

## Running it

No build step is required — just open `index.html` in a browser (or serve the folder with any static web server if HTTP access is needed).

```
index.html
libs/
  lame.min.js
  gifenc.esm.js
```

`libs/lame.min.js` and `libs/gifenc.esm.js` must sit next to `index.html` inside a `libs` subfolder — otherwise MP3 and GIF export won't work.
