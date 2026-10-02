# Published builds registry

The canonical machine-readable publication record is [`published_builds.json`](published_builds.json). Its stable URL is `https://raw.githubusercontent.com/txrx13/meduzavpn/main/releases/published_builds.json`.

## Schema1

The root contains `product: meduza`, `verified_at`, `known_builds`, `channels` and `selection_policy`.

- `known_builds` records version/build, application source SHA, verification time, public release-manifest proof and source-reviewed capability evidence URLs. Its `capabilities` contain `client_actions`, supported `screens` and `screen_requirements`. A known build does not assert publication in every store.
- `channels` identify `platform`, installation channel, publication status, `published_build`/`published_version`, separate `submitted_build`, source SHA, proof URL, verification time, regions and immutable artifact evidence. Installation values are `sideload`, `developer_id`, `none`, `app_store`, `testflight` and `play`.
- Only `status: published` together with a non-null `published_build` asserts public availability. `testers_only`, `review_pending` and `unknown` do not. Null `regions` means country availability is unknown. Null published versions are deliberately not guessed.
- Artifact evidence includes immutable HTTPS URL, exact byte size and SHA-256.

## Current published evidence

The [verified268 record](1.2.49-268.json) identifies the published Android sideload APK, signed Windows installer, and Linux packages/CLI from canonical application main `ca6b69699f419d480bc87a9bdd3484a9ac09100f`. Both versioned and latest public downloads were independently checked by exact SHA256 and byte size. Android release signature/package version, Windows Authenticode publisher/profile/timestamps, and Linux package/repository signatures were verified. The signed Android manifest row was reconciled after official CI publication. Full download-speed checking is opt-in and off by default; the graphical flow uses an exclusive idle-server lease. Linux GUI is amd64; the arm64 files are CLI packages. Apple/store records below remain unchanged; this268 record does not assert a new Apple or store release.

The [263](1.2.45-263.json), [265](1.2.46-265.json) and [verified desktop267 record](1.2.48-267.json) identify actual published sources and artifact evidence. Android APK267 is verified from the successful official [canonical-main CI run](https://github.com/txrx13/meduza-app/actions/runs/36878941268), with both latest and versioned download hashes matched to the release-signed file. Its exact source is recorded per channel and differs from the desktop source; capability declarations are unchanged. Windows installer, macOS Developer ID DMG and Linux graphical **DEB** are verified267. Versioned RPM267 did not match the publisher manifest during verification; this record does not assert its availability or repair it.

macOS TestFlight267 is restricted to internal testers; iOS TestFlight265 remains a beta record. iOS App Store265 and Google Play265 remain review pending. Production macOS App Store publication and regional availability remain unknown.

Known sources263,265 and267 declare the guarded best-location, location-split and restore-purchases capabilities with request/navigation handlers. Exact source evidence URLs are recorded; a capability does not guarantee account entitlement, available products or network success. New confirmation and secure visitor mechanisms under development are not advertised as available.

## Using the record

Current authenticated client capabilities override version inference. A navigation button requiring a capability must be omitted if that capability is absent. Unknown version/channel/region must remain unknown. Installation channel does not establish billing provider or transaction ownership.

Updates require new publication evidence for the exact source, artifact and channel. Direct downloads must never promote store-review or beta records. Publisher verification tooling remains in the application's private repository and requires an explicit metadata target. This public repository contains only published facts, schema and evidence documentation. No new build is published merely by changing this registry.
