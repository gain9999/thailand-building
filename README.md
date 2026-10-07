# Thailand Buildings & Population

Per-province building footprints with heights and per-building population estimates for all 77 Thai provinces, plus a 2D/3D browser viewer (`index.html`).

Live: https://gain9999.github.io/thailand-building/

## Layout

```
index.html                  viewer: buildings / population toggle, 3D extrusion toggle,
                            OSM detail toggle, place search, click a building for
                            its height + estimated residents
provinces.json              index: names, bboxes, building counts, height coverage,
                            2027 population totals, color-scale max, file paths
GlobalBuildingAtlas/        77 × <province>.pmtiles — building footprints, vector tiles z9–15,
                            layer `buildings`, properties:
                              `h` = height in meters where available
                              `plo`, `phi` = estimated resident range (see methodology)
                              `tambon` = subdistrict code
WorldPop/                   77 × <province>_pop2027.tif — 2027 population, 100 m
                            Cloud-Optimized GeoTIFF, people per cell, float32 (source data).
```

Open `index.html` (or the GitHub Pages site) to browse: search for a place or pick a province, pan the map (provinces load automatically), toggle between buildings and population, switch on 3D.

## Population methodology

Each building gets an estimated resident **range** from two sources, computed at **tambon (subdistrict)** level. Each tambon's total — WorldPop 2027 (projection) and DOPA Dec 2025 official registration — is split among its buildings proportional to `footprint area × floors`, where `floors = max(1, round(height_m / 3))` (1 if no height). The viewer shows the low–high range (e.g. ≈ 5–8 residents).
This is a dasymetric estimate: all else equal, bigger/taller buildings get more people.
Caveats: assumes all floor space is residential; building coverage is incomplete in some provinces (the viewer flags these) — per-building numbers there are rough.

## Sources & licenses

- Building footprints: **GlobalBuildingAtlas** (`GBA.ODbLPolygon` + `GBA.Polygon` Part II) — ODbL 1.0 (share-alike)
- Building heights: **GlobalBuildingAtlas** `GBA.LoD1` — CC BY-NC 4.0 (non-commercial)
- 3D detail rendering: © **OpenStreetMap** contributors
- Population (upper): **WorldPop** R2025A 2015–2030, 100 m constrained, 2027 — CC BY 4.0, University of Southampton
- Population (lower): **DOPA** official registration, Dec 2025, tambon level

The height-bearing building files inherit CC BY-NC 4.0 from GBA LoD1.
