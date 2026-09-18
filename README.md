# SecureCode Auditor — fingerprint updates

Signed updates to the known-malware fingerprints used by SecureCode Auditor.

Every fingerprint here was taken from malware found and removed in a real incident:
- payload hashes
- Git blob ids of infected files
- loader campaign ids
- commit messages the campaign used as cover

Installed apps check this feed once a day.

## Why an update can be trusted

- **Signed.** `feed.json.sig` is an Ed25519 signature over `feed.json`. The app accepts it only if it matches the publisher key built into the app. The signature is what makes an update trusted, not this repository or GitHub: an altered file is ignored, wherever it came from.
- **Add-only.** An update can add fingerprints but never remove or change the ones built into the app.
- **Forward-only.** The app refuses a feed older than the one it already has.

## Format

`feed.json`: `format` (1), `version` (an integer that increases), `issued`, and tables of `payload_sha256_16`, `blob_ids`, `campaign_ids`, `infected_commits`, `malware_strings` (exact text, never patterns), `actor_handles` and `commit_subjects`. Every entry carries a short note saying where it was seen.

Fingerprints only: no code, no samples.
