# TajirDZ-Licensing

Central licensing registry for TajirDZ — the **single source of truth** for license state.

Every license record and device-binding state is cryptographically signed (Ed25519). **Any file without a valid trusted signature is INVALID and rejected by the client.** Paths are deterministic and never move when status changes:

- `registry/licenses/<shard>/<licenseId>/license.json` — shard derived from the key lookup digest
- `registry/index/<shard>.json` — digest→licenseId (O(1) lookup) · `registry/index/by-id/<licenseId>.json`
- `registry/device-bindings/<shard>/<licenseId>/<bindingId>.json`

This repository contains **no secrets, no private keys, no customer PII** — only signed technical metadata. Client trust is anchored in a key baked into the official build, never in this repository itself.

Owner operations: the License Administration CLI (not part of client builds).
