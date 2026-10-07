# Thailand Climate-Risk Data — Buildings & Population

Per-province building footprints with heights and 2027 population grids for all 77 Thai provinces, plus a browser viewer (`index.html`).

## Layout

```
index.html                  viewer (buildings / population toggle, click a building for its height)
provinces.json              index: names, bboxes, building counts, height coverage,
                            2027 population totals, color-scale max, file paths
GlobalBuildingAtlas/        77 × <province>.pmtiles — building footprints, vector tiles z9–15,
                            layer `buildings`, property `h` = height in meters where available
                            (1.07M of 2.20M buildings, 48.6%)
WorldPop/                   77 × <province>_pop2027.tif — 2027 population, 100 m
                            Cloud-Optimized GeoTIFF, people per cell, float32.
                            The viewer renders these client-side (geotiff.js); no PNG copies needed.
```

Open `index.html` (or the GitHub Pages site) to browse: pick a province or pan the map, toggle between buildings and population.

## Sources & licenses

- Building footprints: **GlobalBuildingAtlas** `GBA.ODbLPolygon` — ODbL 1.0 (share-alike), © GlobalBuildingAtlas contributors
- Building heights: **GlobalBuildingAtlas** `GBA.LoD1` — CC BY-NC 4.0 (non-commercial)
- Population: **WorldPop** R2025A 2015–2030, 100 m constrained, 2027 — CC BY 4.0, University of Southampton

The height-bearing building files inherit CC BY-NC 4.0 from GBA LoD1.
