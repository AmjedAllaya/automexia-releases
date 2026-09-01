# Distribution boundary

This repository stores public release metadata in Git and signed application
packages as GitHub Release assets. It does not contain Automexia's private source,
build workspace, signing secrets, debug symbols, credentials, or private CI logs.

Publishing is create-once:

1. the private source repository builds and tests native packages;
2. an exact allowlist rejects unowned files and symbols;
3. package hashes, public SBOMs, guidance, and a source-commit-bound manifest are
   assembled;
4. `SHA256SUMS` is signed with the protected minisign key;
5. a repository-scoped, one-hour GitHub App token uploads a draft;
6. the draft asset inventory is verified before publication;
7. the published immutable release is verified again; and
8. the website remains disabled until it receives the exact manifest digest and
   source commit, performs its own live verification, and is reviewed.

This file is the archive's binary-distribution notice; it is not a source-code
license or a grant of additional rights. Each release carries the applicable
notices and terms. Third-party components remain governed by their respective
licenses.
