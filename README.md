# STL Viewer

A simple STL viewer in a single HTML file, built with [three.js](https://threejs.org/).

![Two models side by side in the STL viewer](docs/screenshot.png)

**Use it online:** https://gasille.github.io/simpel-stl-viewer/

Your files stay on your own computer: the viewer reads them in the browser and uploads nothing.

## Usage

1. Open the [online viewer](https://gasille.github.io/simpel-stl-viewer/), or open `index.html` locally in a browser (double-clicking is enough).
2. Click **Open STL** or drag one or more `.stl` files into the window.

Multiple models are placed side by side, at the same scale, each in its own color.

- **Left mouse button**: rotate
- **Right mouse button**: pan
- **Scroll wheel**: zoom
- Buttons: Clear, Wireframe, Grid, Axes, Reset view

The bottom-left panel shows the dimensions (mm) and triangle count of each model.
Both binary and ASCII STL are supported.

> three.js is loaded from jsdelivr, so you need an internet connection.

## Embedding models

A browser is not allowed to load an `.stl` from disk by itself. If you want a page
that shows a model right away, add a script before `<script type="importmap">` that
sets `window.STL_EMBED`:

```html
<script>
  window.STL_EMBED = [
    { name: "model.stl", base64: "<base64 of the STL file>" }
  ];
</script>
```

A single object instead of an array also works.

## License

[MIT](LICENSE). three.js is covered by its own MIT license.
