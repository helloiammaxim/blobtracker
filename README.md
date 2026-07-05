# BLOBTRACKER

Browser-based blob tracking effects for video. Load footage, overlay animated tracking markers, export — all client-side, single HTML file, no server or install.

## How to use

1. **Open** `blobtracker.html` in Chrome or Edge.
2. **Load a video** — drag & drop onto the canvas or click "Load video".
3. **Tune detection (01)** — pick what counts as a blob: bright areas, dark areas, a keyed color, or motion. Adjust threshold until the right things are tracked (enable "show detection mask" to see exactly what's detected). Use min/max area to filter noise, smoothing to stabilize jitter.
4. **Style markers (02)** — choose a tracker shape (rect, circle, cross, l-frame, scope, corner handles, etc.), base size, and a size mode: fixed, or driven by blob lightness, area, speed, or hue.
5. **Connections (03)** — lines between nearby blobs: how many per blob, min/max distance, straight/curved/elbow, width, gaps, fade.
6. **Labels (04)** — ID, coordinates, area, speed, or custom text in Space Grotesk. Position at frame corner, center, above, or below.
7. **Trails (05)** — optional motion paths, up to the full clip length; colored by a fixed color, the blob, or the background.
8. **Set the effect range** — drag the two handles on the timeline to choose where the effect is active; FADE IN / FADE OUT gradually ramp the blob count at the edges.
9. **Export** — pick a mode (full composite, blobs on black, blobs transparent) and format, then hit "Export video". A download link appears when done.

## Export formats

- **WebM** — native, fastest, supports alpha transparency
- **MP4 / MOV** — recorded natively where the browser supports it, otherwise converted in-browser via ffmpeg.wasm (~25 MB one-time download); opaque only
- **PNG sequence (ZIP)** — true alpha, frame-exact, exports only the FX range; best for After Effects / Blender

WebM/MP4 export records in real time — keep the tab focused. For MP4/MOV conversion, run from a local server instead of `file://`:

```
python -m http.server
# → http://localhost:8000/blobtracker.html
```

## Notes

- Dark and light themes (◐ button), follows system preference by default
- Works on mobile — touch-optimized controls, stacked layout
- Stack: vanilla JS, Canvas 2D, MediaRecorder, JSZip, ffmpeg.wasm — no build step

## License

**In simple words:**

- ✅ Use it for anything — personal projects, client work, commercial videos, paid productions
- ✅ Modify it, remix it, share it
- ❌ Don't sell or offer BLOBTRACKER itself (or a rebranded copy) as your own tool, product, or service

Basically: make cool stuff with it, earn money with what you make — just don't sell the tool.

Full terms: [PolyForm Perimeter 1.0.1](LICENSE.md). Want to build a product on it? Get in touch: [@helloiammaxim](https://instagram.com/helloiammaxim)
