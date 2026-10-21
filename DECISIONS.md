# Decisions

Dated, irreversible-leaning decisions, one entry each, newest last. The
reasoning lives in `PLAN.md`.

**What counts as one-way in a data repository**: a decision that puts bytes in
readers' hands under a shape they will code against; a decision about which
repository owns a product, since moving one costs a migration in two places;
and a decision that forecloses an upstream.

## D1 — 2026-10-20 — Its own repository, R2 alone, the archives sent by the jobs that build them

ESA WorldCover gets a repository of its own (2026-10-20) and **publishes to Cloudflare R2 alone**, as every new product since the site pipeline's D13: Pages carries its status alone. The set — about 160 GB in 508 archives — is past any runner's disk, so each matrix job sends the cells it builds to R2 itself; the run writes the index that names them, and the R2 publish lands it only once every one is there.
