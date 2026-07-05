# BLOBTRACKER

Browser-based blob tracking effects for video. Load footage, overlay animated tracking markers, export — all client-side, no server, single HTML file.

![dark & light themes · Space Grotesk HUD aesthetic](docs/preview.png)

## Features

- **Detection** — by brightness, darkness, color key, or motion (frame diff). Threshold, sample resolution, min/max blob area, blob count (up to 5000), position smoothing, debug mask overlay. Blobs are tracked across frames with stable IDs and velocity.
- **Markers** — 15 tracker types: rect, circle, x-rect, cross, dot (round/square), l-frame, scope, grid, corner handles (square/circle), diamond, triangle, brackets, ring. Size modes: fixed, lightness, area, speed, hue. Line width, handle dot size, fixed or blob-sampled color, rotation by motion.
- **Connections** — per-blob count, min/max distance, straight / curved / elbow lines, width, endpoint gaps, distance-based opacity fade, dashed.
- **Labels** — Space Grotesk. ID, coordinates, area, speed, or custom text. Corner / center / above / below positioning, size, offset, background plate.
- **Trails** — up to full clip length. Color: fixed, from blob, or sampled from background.
- **Timeline** — draggable FX in/out range, gradual blob count fade in/out.
- **Export**
  - WebM (native, supports alpha transparency)
  - MP4 / MOV via native MediaRecorder or in-browser ffmpeg.wasm
  - PNG sequence (ZIP) with true alpha — for After Effects / Blender compositing
  - Modes: full composite, blobs on black, blobs on transparent

## Usage

Open `blobtracker.html` in Chrome/Edge. That's it.

For MP4/MOV conversion (ffmpeg.wasm workers), serve locally instead of `file://`:

```
python -m http.server
# → http://localhost:8000/blobtracker.html
```

## Notes

- Alpha transparency: WebM (Chrome, Blender) or PNG sequence (everything). H.264 MP4/MOV is opaque.
- WebM/MP4 export records in real time — keep the tab focused. PNG sequence is seek-driven and drop-proof.
- ffmpeg.wasm (~25 MB) loads lazily from CDN on first MP4/MOV convert.
- Mobile-optimized: touch targets, stacked layout, reduced default detection resolution.

## Stack

Vanilla JS, Canvas 2D, MediaRecorder, JSZip, ffmpeg.wasm. No build step, no dependencies to install.

## License

MIT
