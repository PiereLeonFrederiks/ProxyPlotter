# Stratigraphic Proxy Plotter

A single-file, offline-capable web app for plotting depth-resolved proxy and laboratory data against a stratigraphic column. Built as a companion to the **Geoarchaeological Core Logger**, it turns measurement tables (grain size, loss-on-ignition, geochemistry, …) into publication-ready proxy diagrams, optionally aligned to the lithology of a logged core. It runs entirely in the browser with no server or installation required.

To the application: https://piereleonfrederiks.github.io/ProxyPlotter/

⚠ Early Access — This project is under active development. Features, exports, and data formats may change between versions. If you use this tool, I'd love to hear what works, what doesn't, and what's missing.

DOI: <https://doi.org/10.5281/zenodo.21023813>

---

## Features

### Proxy Data Plotting

- Load a measurement table and plot one or more variables as panels against a shared **depth axis**
- First column is read as **depth (m)**; every other column becomes a plottable variable (e.g. grain size, LOI, XRF element counts, pH, TOC)
- Per-variable **plot styles**: line, line + points, points only, bars / histogram, silhouette (filled curve), blended band (smooth curve), and colour blocks per layer
- Per-variable **value axis**: min/max range, axis position (top or bottom of panels), and units in the header
- **Sample tick marks** show where each measured depth falls, so data density stays visible

### Stratigraphic Integration (Core Logger Addon)

- Optionally drop in a **Core Logger profile** to render the matching **lithology column** beside the proxy panels
- **Layer boundary lines** carried from the profile extend across the panels, so proxy values line up with the stratigraphy
- A **Finds & observations column** mirrors the Core Logger's find categories (samples, shells, charcoal, wood, ceramics, humic concentrations, roots, stones, iron oxide), with configurable display (markers only, markers + labels, or labels only)
- Lithology background can be drawn from the profile's colours, a flat fill, or an uploaded depth → colour table

### Correlation & Facies

- **Auto-correlate** scans the loaded proxies and **suggests facies / horizon boundaries**; each suggestion can be accepted as a horizon or dismissed
- **Add horizon at depth** to place boundaries manually; horizons are drawn across all panels
- **Section brackets**: group several columns under a labelled bracket (e.g. "Grain size") to organise a wide diagram into logical blocks

### Column Management

- Reorder columns by dragging the **▲▼** handles
- **Recolour** any variable by clicking its swatch
- **Hide / show** a column with the eye toggle without removing its data
- Group columns into stacks (A / B / C) or leave them ungrouped

### Display & Styling

- **Publication-style preset** for clean, print-ready output in one click
- Configurable **depth axis**, depth direction (0 at top, increasing downward — or reversed), **depth grid lines**, vertical grid lines within panels, and grid style (solid / dashed / dotted)
- Adjustable **line weight**, **density**, and **resolution**
- Toggle value axes & ticks, layer boundary lines, horizons, and section brackets independently

---

## Data Input

| Source                   | Format                                                                        |
| ------------------------ | ----------------------------------------------------------------------------- |
| **Proxy data**           | CSV / TSV / TXT — **first column = depth (m)**, remaining columns = variables |
| **Core Logger profile**  | A profile exported from the Core Logger (JSON), for the lithology + finds columns |
| **Depth → colour table** | CSV / TSV — first column = depth (m), second = colour (hex), for custom lithology shading |

Files are loaded by **drag-and-drop** onto the matching drop zone, or by clicking to browse. JSON profiles and `.json`-style content are detected automatically.

---

## Export Formats

| Format               | Description                                          |
| -------------------- | ---------------------------------------------------- |
| **Export data (CSV)** | The assembled dataset as CSV for archiving or reuse |
| **JPG / PNG**        | Raster image of the proxy diagram                    |
| **SVG**              | Vector export of the diagram                         |

Raster exports offer selectable resolution — **96 dpi (screen)**, **150 dpi**, **300 dpi (print)**, and **600 dpi (poster)** — for figures sized to journals or large-format printing.

---

## Usage

1. Open `index.html` in any modern browser — no installation, no internet required after the first load (fonts load from Google Fonts on first use)
2. **Drop a CSV/TSV** with a depth column and one or more proxy variables
3. Optionally **drop a Core Logger profile** to show the matching lithology and finds columns alongside the data
4. Choose plot styles, set value-axis ranges, reorder and recolour columns, and add horizons or section brackets as needed
5. Apply the **publication-style preset** and export as SVG/PNG/JPG, or export the assembled data as CSV

---

## Companion Tool — Geoarchaeological Core Logger

The Proxy Plotter is designed to pair with the **Core Logger**, which records the core stratigraphy itself (layers, Munsell-aware colours, KA5/DIN classification, gradational shifts, finds, and compaction zones). A profile exported from the Core Logger drops straight into the Proxy Plotter to provide the lithology and finds columns next to your measurement data, so the two tools together produce a complete, aligned proxy figure.

---

## Mobile Support

The app is optimised for tablet and phone use:

- Responsive layout with touch-friendly input sizes
- Drag-and-drop file loading with a click-to-browse fallback for touch devices
- The plot-style dropdowns and reordering handles are adapted for narrow / touch layouts

---

## File Structure

The entire application is a single self-contained `index.html` file. All styles, logic, and rendering are inlined — no external dependencies beyond the Google Fonts stylesheet.

---

## Browser Compatibility

| Browser                           | Support |
| --------------------------------- | ------- |
| Chrome / Edge (desktop & Android) | ✅ Full  |
| Firefox (desktop)                 | ✅ Full  |
| Safari (macOS)                    | ✅ Full  |
| Safari (iOS)                      | ✅ Full  |

Uses modern JavaScript; very old browsers (pre-2018) are not supported.

---

## License

See repository or contact the author for licensing information.

## Credits

Developed by PLF. AI-assisted development — Claude (Anthropic) was used during parts of the scripting process.
