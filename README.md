# Export2KMZ — QGIS 3 plugin

Exports selected vector layers from the current QGIS project to Google Earth KMZ.

## Features
- Exports point, line, polygon, and multipart vector geometries.
- Reprojects output coordinates to EPSG:4326.
- Follows the QGIS layer-tree order and preserves nested group hierarchy.
- Configurable per-layer folder suffix: feature count, numeric field sum, or no statistic.
- Numeric field sums ignore null/empty values, preserve decimal precision, and report non-numeric values instead of silently treating them as zero.
- For every attribute-based classification, appends the category feature count (for example, `Category A=25`); `SUB BOX` retains its `Type` classification and labels such as `SUB BOX(70/30)=8`, `SUB BOX(50/50)=4`, and `END BOX=4`.
- Provides an optional, unchecked-by-default **汇总 UNITS 字段** checkbox. When enabled, the six selected HOMES layers (`Sdus`, `Mdus`, `Church`, `Commercial`, `Hospitals`, `Institution`) are summed by their `UNITS` fields, and the total is appended to their nearest common existing QGIS group name. It does not create a new group or rename the source QGIS group/layers.
- Supports per-layer Description field selection and optional ExtendedData attributes.
- Supports same-name layer synchronization for statistic mode, sum field, and Description field. A target with missing fields is left unchanged and reported separately.
- Saves export configuration in the current QGIS project; save the QGIS project to retain settings between sessions.
- Retains JSON style-template import/export.

## Layer statistics
Each layer can independently use one of three modes:
- **Feature count**: `LayerName=100`
- **Field sum**: `LayerName=1010`
- **No statistic**: `LayerName`

There is no forced HOMES `UNITS` sum. Select the required numeric field separately for each layer. The separate **汇总 UNITS 字段** checkbox is an optional project-specific group summary and is off by default. When enabled, all six HOMES layers must be selected for export and share an existing parent group. The SUB BOX Type classification remains available.

## Installation
Download the latest `Export2kmz.zip` from the repository's **Releases** page. Extract the ZIP into your QGIS profile's `python/plugins/` directory so that the `Export2kmz` folder is directly inside `python/plugins/`. Restart QGIS and enable Export2KMZ in Plugins → Manage and Install Plugins.

## Build
GitHub Actions packages the root plugin files into an installable `Export2kmz/` directory and publishes the ZIP as the latest release.
