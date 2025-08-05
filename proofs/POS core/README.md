# Public Proof of Development Archive

This repository contains cryptographic proof that the file `PosCore.bundle` (not publicly shared due to IP restrictions) existed and was authored by me at a specific time.

`PosCore.bundle` is a generated from POS Core

- `PosCore.bundle.hash` is the SHA-256 fingerprint
- `PosCore.bundle.hash.sig` is a detached GPG signature by Emilio M. Guevara
- `gpg_pubkey.asc` is my public key for signature verification

The original bundle was created on 2025-08-04. Any tampering with the original .bundle will break hash verification. If the bundle no longer exists, its hash serves as a tamper-evident fingerprint — the content can only be proven authentic if the .bundle can be exactly reproduced.
