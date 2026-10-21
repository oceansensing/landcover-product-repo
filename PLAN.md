# landcover-product-repo: the founding plan and running record

The world's **land cover**, as tile archives. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Published since 2026-10-21** (below); daily at 09:41 UTC since then, and an
unchanged source builds and sends nothing.

## What it is for

One product, R2's alone: **`worldcover`** (`worldcover.json`, `map/land/worldcover/`) — ESA WorldCover 2021 v200 as 256-pixel palette PNGs in Web Mercator (the XYZ scheme), zooms 0 to 14, each pixel a class's palette index (0, no data — the sea among it — clear; the eleven classes in ESA's own colors), packed into PMTiles archives (version 3, directories gzipped, tiles clustered): `overview.pmtiles`, zooms 0 to 4, and `cells/5-<x>-<y>.pmtiles`, one for each zoom-5 cell the land touches (507), its zooms 5 to 14, each beside its zoom-5 tile and its build's record. Zoom 14 is the source sampled at each pixel's center; each zoom above takes the class most of the four beneath hold. The index names every archive with its MD5; the set's version is the source's identity and the tiling's, so an unchanged source builds nothing new.

## Where the data comes from

**ESA WorldCover 10 m 2021 v200** (2,651 cloud-optimized GeoTIFFs of 3°, 124 GB, on AWS's open data registry, `s3://esa-worldcover/v200/2021/map/`, read over HTTPS without a key), by the ESA WorldCover consortium from Sentinel-1 and Sentinel-2. **CC BY 4.0**; a map showing it carries *"© ESA WorldCover project 2021 / Contains modified Copernicus Sentinel data (2021) processed by ESA WorldCover consortium"*. Citation: Zanaga, D. et al. (2022), ESA WorldCover 10 m 2021 v200, https://doi.org/10.5281/zenodo.7254221. Overall accuracy 76.7% (its Product Validation Report v2.0). The files are final: ESA's project ended with 2021, and Copernicus's Land Cover and Tropical Forest Monitoring service carries it on. Terms read 2026-10-20.

## Open

1. Copernicus's LCFM years, as they are released: a set a year, the same archives.

## Record

- **2026-10-21, the first run** ([39526857129](https://github.com/oceansensing/landcover-product-repo/actions/runs/39526857129),
  dispatched 2026-10-21 01:21 UTC, green 04:09): the plan read version `d124dbe572b2`; 32 groups, eight at a time,
  26–50 minutes each, every group building the cells it planned — 453 cells with land sent to R2 as they were
  built, 54 of the sea alone recorded and skipped, the largest `5-18-17` at 1.87 GB; the build read the 960 cell
  files back and wrote the index: 453 cells, 84,462,248 tiles, 167.4 GB; the R2 publish landed the index only once
  every archive it names was there with its MD5. The daily schedule turned on the same morning.
