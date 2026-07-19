# SampleDetect Catalog

This public repository hosts the versioned sample-lineage database used by the
SampleDetect iOS app.

## Published files

- `manifest.json` tells installed apps which catalog version is current, where
  to download it, and the expected SHA-256 checksum.
- `samples.sqlite` is the compact, read-only catalog bundled from SampleDetect's
  curated entries and open MusicBrainz-derived relationships. It includes an
  indexed graph projection for bidirectional Music DNA exploration.
- `release-info.json` records the database schema, catalog counts, input hashes,
  and integrity result for the current immutable release.

The app downloads a catalog only when the manifest version increases, verifies
its checksum and schema compatibility, installs it atomically, and keeps the
bundled database as a fallback.

## Current release

Catalog v3 uses SQLite schema v3 and normalization contract v2:

- 14,875 sample-indexed destination songs
- 32,715 recording/source nodes
- 24,312 recording-level sample relationships
- 24,400 source assertions
- 16,478 ISRC-resolved nodes
- 32,659 nodes with structured artist credits
- 19,375 recording-to-work links

The v3 database passed `PRAGMA integrity_check`, has zero foreign-key errors,
and is published under the immutable `catalog-v3` Git tag before the main
manifest is advanced.

## Data notes

The catalog combines factual, hand-curated sample relationships with
MusicBrainz-derived data. MusicBrainz data is provided under its applicable
open-data terms. This repository is intentionally separate from the private app
source repository so released catalogs can be downloaded without credentials.
