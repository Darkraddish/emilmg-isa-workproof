# Proof of Involvement (Good Faith Statement)

This repository contains cryptographically signed files intended as **proof of authorship and involvement** in the development of this project. The goal is to establish transparency and accountability — not to create conflict, accusations, or reputational harm.

## Intent

These materials are published in good faith:
- To demonstrate my role and participation in the work.
- To ensure the technical history is preserved and attributable.
- To protect my authorship over unmodified contributions.

## Signature Hierarchy

- **GPG-signed files** (e.g., `.sig`, `.asc`) carry **stronger weight** as verifiable cryptographic evidence.
- **Unsigned files** (e.g., this `README.md`) are supportive but carry **less evidentiary weight** and are included for context and transparency.

## Proof Start Point

The verifiable chain of authorship begins with the first commit I signed using GPG. All previous unmodified commits before that point are still attributable via Git metadata and commit consistency, but lack cryptographic proof.

## Finalization Protocol

At the conclusion of my involvement:
- A **complete Git commit log** (`git log --pretty=fuller`) will be generated for each project repository.
- This log will be **GPG clearsigned** to preserve its integrity and authorship.
- The signed log will be stored and committed to a dedicated **proofs folder** in my archive — one file per project.
- This step ensures that my contributions can be verified independently of the original repository’s future state or availability.


## Note

These proofs are not intended for public blame or assertion of ownership beyond what is provable and reasonable. They exist to clarify authorship, protect contributors, and promote a culture of accountable collaboration.

---

# Proof Generation Procedure
This guide outlines the step-by-step process to generate proof of authorship, commit integrity, and repository traceability for archival or public defense purposes.

## File Naming Convention

| File Name            | Description                             |
| -------------------- | --------------------------------------- |
| `project.bundle`     | Git bundle of the repository            |
| `bundle.sig`         | Detached GPG signature of the bundle    |
| `commit-log.txt.asc` | GPG clearsigned commit log              |
| `bundle.hash.asc`    | SHA256 hash of the bundle               |
| `README.md`          | Repository metadata and integrity notes |

## Procedure
**Create bundle and commit log from project directory to proof directory.**
### Bundle the Repository

```bash
git bundle create "./path/to/folder/project.bundle" --all
```
### Create Commit Log

```bash
git log --pretty=fuller > "./path/to/folder/commit-log.txt"
```


**Open Git Bash in the proof directory and** proceed on signing the files
### Hash the Bundle

```bash
sha256sum project.bundle > bundle.hash
```

### `Clearsign` the files

```bash
gpg --clearsign bundle.hash
gpg --clearsign commit-log.txt
```
### Detached Signature of the Bundle

```bash
gpg --output bundle.sig --detach-sign project.bundle
```

### Cleanup for IP Concerns

Only retain the following:
- `bundle.hash.asc`
- `commit-log.txt.asc`
- `README.md`
- `bundle.sig`

Delete any of the following if temporarily created:
- `project.bundle`
- The full `.git` repo clone
- Intermediate `.md` files (unsigned)

## README Template

``` markdown

# Project Integrity Proof

This folder contains a self-contained proof of the repository’s state and authorship.
## Contents
- `bundle.sig` — GPG detached signature of the bundle
- `bundle.hash.asc` — GPG `Clearsigned` SHA256 hash of the bundle in plain text
- `commit-log.txt.asc` — GPG `Clearsigned` commit history

## Verification Steps

1. **Verify bundle hash:**
	`sha256sum -c bundle.hash.asc`


2. **Verify commit log:** 
	`gpg --verify commit-log.txt.asc`

## Notes
> 📌 Reconstructed Proof Notice:  
> These proof files were recreated on [YYYY-MM-DD] for verification. All content reflects the true repository state.

> ✍️ Author: Emilio M. Guevara  
> Commits and bundles are timestamped and signed where applicable.

```

### 🗒️ Optional README Notes

You may add:
- **Reconstruction Notice** – clarify if the bundle/signature was rebuilt after initial push.
- **Commit Signature Statement** – e.g., “All commits authored by me and verifiable via GPG log.”
- **Personal Notes** – comments on the project state, intent of push, or archival purpose.