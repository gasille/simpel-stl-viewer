# STL Viewer

A simple STL viewer in a single HTML file, built with [three.js](https://threejs.org/).

![Two models side by side with dimensions and a measurement](docs/screenshot.png)

**Use it online:** https://gasille.github.io/simple-stl-viewer/

Your files stay on your own computer: the viewer reads them in the browser and uploads nothing.

## Usage

1. Open the [online viewer](https://gasille.github.io/simple-stl-viewer/), or open `index.html` locally in a browser (double-clicking is enough).
2. Click **Open STL** or drag one or more `.stl` files into the window.

Multiple models are placed side by side, at the same scale, each in its own color.

- **Left mouse button**: rotate
- **Right mouse button**: pan
- **Scroll wheel**: zoom
- Buttons: Clear, Overlay, Dimensions, Measure, Lay flat, Overhangs, Wireframe, Grid, Axes, Reset view

**Dimensions** draws a bounding box around each model with dimension lines and
labels for its length (X), width (Y) and height (Z) in mm.

**Measure** lets you click two points on a model to see the distance between
them, plus the difference along X, Y and Z. A point snaps to a nearby corner of
the mesh, so you can measure edges precisely. You can still rotate and zoom while
measuring, add as many measurements as you like, and press **Esc** to cancel a
half-finished one. Turning Measure off clears all measurements.

### Preparing a print

- **Overhangs** colors every surface steeper than 45° red: those are the places
  that need support. The model panel shows the overhang area in cm². Surfaces
  resting on the bed are not counted.
- **Lay flat**: turn it on and click a face; the model rotates so that face lies
  on the bed. Combine it with Overhangs to find an orientation with as little red
  as possible. The **↺** button in the model panel restores the original
  orientation.
- **Printer** (dropdown at the end of the toolbar): pick a printer (Bambu Lab A1
  mini, A1/P1S/X1C, Prusa MK4, Prusa MINI, Creality Ender 3, or a custom size) to
  show its build volume. The model panel says per model whether it fits, also
  when turned 90° on the bed.

### Comparing models

**Overlay** places all models on top of each other, semi-transparent, so you can
see exactly where two versions of a part differ. Click it again to go back to
side by side.

### Model panel

The bottom-left panel lists every model with:

- a color swatch (click to change the color),
- **Hide/Show** and **✕** (remove just this model),
- dimensions (mm) and triangle count,
- volume (cm³) and an estimated weight for the material chosen in the toolbar
  (PLA, PETG, ABS, ASA, TPU or resin).

The weight assumes a solid print (100% infill), so a real print with less infill
will be lighter. Volume is only accurate for closed (watertight) meshes.

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
