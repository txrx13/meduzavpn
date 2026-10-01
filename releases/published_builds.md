# Published builds registry

The canonical machine-readable publication record is [`published_builds.json`](published_builds.json). Its stable URL is `https://raw.githubusercontent.com/txrx13/meduzavpn/main/releases/published_builds.json`.

## Schema1

The root contains `product: meduza`, `verified_at`, `known_builds`, `channels` and `selection_policy`.

- `known_builds` records version/build, application source SHA, verification time, public release-manifest proof and source-reviewed capability evidence URLs. Its `capabilities` contain `client_actions`, supported `screens` and `screen_requirements`. A known build does not assert publication in every store.
- `channels` identify `platform`, installation channel, publication status, `published_build`/`published_version`, separate `submitted_build`, source SHA, proof URL, verification time, regions and immutable artifact evidence. Installation values are `sideload`, `developer_id`, `none`, `app_store`, `testflight` and `play`.
- Only `status: published` together with a non-null `published_build` asserts public availability. `testers_only`, `review_pending` and `unknown` do not. Null `regions` means country availability is unknown. Null published versions are deliberately not guessed.
- Artifact evidence includes immutable HTTPS URL, exact byte size and SHA-256.

## Current published evidence

The existing [263 release manifest](1.2.45-263.json) and [265 release manifest](1.2.46-265.json) establish source and artifact provenance. [265 publication notes](1.2.46-265.md) distinguish direct publication, TestFlight and production store review. Direct Android APK, macOS DMG, Windows installer and Linux graphical package are published265. The same release manifest documents CLI/package/router artifacts.

TestFlight265 is limited to testers on iOS/macOS. iOS App Store265 and Google Play265 are recorded as review pending; no production availability is inferred. macOS App Store publication and regional availability are unknown. Proposed development builds are absent.

Published source263 (`71e3c354a664c6a46d9ce2eb9c9baf49add97919`) and265 (`958f84f59155d06c66a453ab0277bed92e0914dd`) both declare the guarded best-location, location-split and restore-purchases capabilities and contain their corresponding request/navigation handlers. The JSON contains exact source evidence URLs; capability presence does not guarantee account entitlement, available products or network success.

## Using the record

Current authenticated client capabilities override version inference. A navigation button requiring a capability must be omitted if that capability is absent. Unknown version/channel/region must remain unknown. Installation channel does not establish billing provider or transaction ownership.

Updates require new publication evidence for the exact source, artifact and channel. Direct downloads must never promote store-review or beta records. Publisher verification tooling remains in the application's private repository and requires an explicit metadata target. This public repository contains only published facts, schema and evidence documentation. No new build is published merely by changing this registry.
