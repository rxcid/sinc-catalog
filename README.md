# Sinc Catalog

This public repository hosts the versioned sample-lineage database used by the
Sinc iOS app.

## Published files

- `manifest.json` tells installed apps which catalog version is current, where
  to download it, and the expected SHA-256 checksum.
- `samples.sqlite` is the compact, read-only catalog bundled from Sinc's
  curated entries and open MusicBrainz-derived relationships. It includes an
  indexed graph projection for bidirectional Music DNA exploration.

The app downloads a catalog only when the manifest version increases, verifies
its checksum, and keeps the bundled database as a fallback.

Catalog databases are published as immutable GitHub Release assets before
`main/manifest.json` is updated. The historical tagged database snapshots remain
available for verification and rollback.

## Legacy compatibility

The former `rxcid/sample-detect-catalog` repository remains online for app
builds that were compiled before the Sinc catalog migration. Do not delete or
reuse that repository name while those builds may still be in use.

## Data notes

The catalog combines factual, hand-curated sample relationships with
MusicBrainz-derived data. MusicBrainz data is provided under its applicable
open-data terms. This repository is intentionally separate from the private app
source repository so released catalogs can be downloaded without credentials.
