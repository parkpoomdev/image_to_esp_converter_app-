# Image → EPS Converter (Client-side)

A tiny, single-file web app to convert JPG/PNG images to EPS (Encapsulated PostScript) entirely in the browser. No uploads. Drag-and-drop supported.

> Note: You mentioned "ESP". This app outputs `.eps`. If you really require `.esp`, please clarify the exact format you need.


<img width="1047" height="825" alt="image" src="https://github.com/user-attachments/assets/9ab865f2-2737-4418-96bd-188d9e3322e7" />

## Quick Start

- Open `index.html` in your browser (no server required), or serve the folder with any static server.
- Drag and drop a `.jpg`/`.jpeg`/`.png` file, or click Browse.
- Optionally set a maximum dimension to resize the image.
- Click "Convert to EPS" and then "Download .eps".

## How it works

- The image is drawn onto a Canvas (white background for PNG transparency).
- Pixel data (RGB) is embedded as hex in a minimal EPS with `colorimage` operator.
- Output is raster-in-EPS (not vectorized). For vectorization, a separate tracing step/tool is required.

## Tips

- Large images produce large `.eps` files and take longer to generate. Consider setting a reasonable "Max dimension" (e.g. 2048).
- Output filename defaults to the original name with `.eps` extension; you can change it.

## Limitations

- Alpha channel (transparency) is flattened to white.
- EPS file is not compressed.
- This is a minimal EPS; some very old workflows may expect additional DSC comments.

## Local static server (optional)

If you prefer serving over HTTP instead of opening the file directly:

```powershell
# From the project folder
# Option 1: Python (if installed)
python -m http.server 8080

# Option 2: Node 'http-server' (if installed)
# npm install -g http-server
http-server -p 8080
```

Then open http://localhost:8080 in your browser and navigate to `index.html`.
