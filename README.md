# landcover-product-repo

The world's **land cover**, as tile archives: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Nothing is published yet.** `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

One product, R2's alone: **`worldcover`** (`worldcover.json`, `map/land/worldcover/`) — ESA WorldCover 2021 v200 as 256-pixel palette PNGs in Web Mercator (the XYZ scheme), zooms 0 to 14, each pixel a class's palette index (0, no data — the sea among it — clear; the eleven classes in ESA's own colors), packed into PMTiles archives (version 3, directories gzipped, tiles clustered): `overview.pmtiles`, zooms 0 to 4, and `cells/5-<x>-<y>.pmtiles`, one for each zoom-5 cell the land touches (507), its zooms 5 to 14, each beside its zoom-5 tile and its build's record. Zoom 14 is the source sampled at each pixel's center; each zoom above takes the class most of the four beneath hold. The index names every archive with its MD5; the set's version is the source's identity and the tiling's, so an unchanged source builds nothing new.

These products are published **operationally but not drawn on the website's map**; the map's status
line still reports them when they fall behind, which is how their health stays visible.

## Where the data comes from

**ESA WorldCover 10 m 2021 v200** (2,651 cloud-optimized GeoTIFFs of 3°, 124 GB, on AWS's open data registry, `s3://esa-worldcover/v200/2021/map/`, read over HTTPS without a key), by the ESA WorldCover consortium from Sentinel-1 and Sentinel-2. **CC BY 4.0**; a map showing it carries *"© ESA WorldCover project 2021 / Contains modified Copernicus Sentinel data (2021) processed by ESA WorldCover consortium"*. Citation: Zanaga, D. et al. (2022), ESA WorldCover 10 m 2021 v200, https://doi.org/10.5281/zenodo.7254221. Overall accuracy 76.7% (its Product Validation Report v2.0). The files are final: ESA's project ended with 2021, and Copernicus's Land Cover and Tropical Forest Monitoring service carries it on. Terms read 2026-10-20.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: none it depends on.

**Which document gets what, and what "update docs" means across all
thirty-three repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all thirty-three, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
