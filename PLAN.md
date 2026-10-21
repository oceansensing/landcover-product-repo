# landcover-product-repo: the founding plan and running record

The world's **land cover**, as tile archives. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Nothing is published yet.**

## What it is for

One product, R2's alone: **`worldcover`** (`worldcover.json`, `map/land/worldcover/`) — ESA WorldCover 2021 v200 as 256-pixel palette PNGs in Web Mercator (the XYZ scheme), zooms 0 to 14, each pixel a class's palette index (0, no data — the sea among it — clear; the eleven classes in ESA's own colors), packed into PMTiles archives (version 3, directories gzipped, tiles clustered): `overview.pmtiles`, zooms 0 to 4, and `cells/5-<x>-<y>.pmtiles`, one for each zoom-5 cell the land touches (507), its zooms 5 to 14, each beside its zoom-5 tile and its build's record. Zoom 14 is the source sampled at each pixel's center; each zoom above takes the class most of the four beneath hold. The index names every archive with its MD5; the set's version is the source's identity and the tiling's, so an unchanged source builds nothing new.

## Where the data comes from

**ESA WorldCover 10 m 2021 v200** (2,651 cloud-optimized GeoTIFFs of 3°, 124 GB, on AWS's open data registry, `s3://esa-worldcover/v200/2021/map/`, read over HTTPS without a key), by the ESA WorldCover consortium from Sentinel-1 and Sentinel-2. **CC BY 4.0**; a map showing it carries *"© ESA WorldCover project 2021 / Contains modified Copernicus Sentinel data (2021) processed by ESA WorldCover consortium"*. Citation: Zanaga, D. et al. (2022), ESA WorldCover 10 m 2021 v200, https://doi.org/10.5281/zenodo.7254221. Overall accuracy 76.7% (its Product Validation Report v2.0). The files are final: ESA's project ended with 2021, and Copernicus's Land Cover and Tropical Forest Monitoring service carries it on. Terms read 2026-10-20.

## Open

1. The first dispatched run, read: the plan, the matrix's groups and their times, the build reading every cell back, the index landing on R2.
2. Then the daily schedule.
3. Copernicus's LCFM years, as they are released: a set a year, the same archives.
