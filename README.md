# Export2KMZ — QGIS 3 plugin

Exports selected vector layers from the current QGIS project to a Google Earth KMZ file.

## Features
- Point, line, polygon, and multipart vector geometry export.
- Reprojects output coordinates to EPSG:4326.
- Preserves the existing QGIS layer-tree group hierarchy in KML/KMZ.
- Adds `=feature_count` to every exported layer Folder, including empty layers (`=0`).
- For `SUB BOX`, counts features by the `Type` field and writes compact child Folder names such as `SUB BOX(70/30)=8`, `SUB BOX(50/50)=4`, and `END BOX=4`.
- For `Sdus`, `Mdus`, `Church`, `Commercial`, `Hospitals`, and `Institution`, sums the `UNITS` field and appends the total, e.g. `Sdus=1010`.
- Retains the layer's existing placemark Name, geometry, selected Description field, and optional ExtendedData attributes.
- Keeps renderer categories with zero features in the SUB BOX Type folders when those categories exist in the QGIS categorized renderer.
- Supports style templates and per-layer Description field selection.

## ODN naming rules
- Ordinary layers: `LayerName=feature_count`
- SUB BOX parent: `SUB BOX=feature_count`
- SUB BOX Type children: `SUB BOX(70/30)=count`, `SUB BOX(50/50)=count`, `END BOX=count`
- HOMES PASS children: sum `UNITS`, not point feature count.
- Folder hierarchy follows the selected layer's current QGIS layer-tree parent groups, such as `KIM-HB10/HOMES PASS/Sdus=1010`.

## Installation
Download the latest `Export2kmz.zip` from the repository's **Releases** page. Extract the ZIP into your QGIS profile's `python/plugins/` directory so that the `Export2kmz` folder is directly inside `python/plugins/`. Restart QGIS and enable Export2KMZ in Plugins → Manage and Install Plugins.

## Build
GitHub Actions packages the root plugin files into an installable `Export2kmz/` directory and publishes the ZIP as the latest release.
