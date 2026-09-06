<p><img src="assets/automexia-logo.png" width="40" height="40" alt="Automexia logo"></p>

# Verify your download

[Downloads](README.md#download-linux-v040) · [Install](INSTALL.md) · [Security](SECURITY.md)

Verify **before** installing or running a package. A checksum detects changed
bytes; a signature also binds the checksum list to a trusted signing key.
Neither proves that software is free of vulnerabilities.

## 1. Get the verification files

Save your chosen package and both files below in the same new, empty folder:

- [SHA256SUMS](https://github.com/AmjedAllaya/automexia-releases/releases/download/v0.4.0/SHA256SUMS)
- [SHA256SUMS.minisig](https://github.com/AmjedAllaya/automexia-releases/releases/download/v0.4.0/SHA256SUMS.minisig)

These instructions use [Minisign](https://jedisct1.github.io/minisign/) and GNU
`sha256sum`. Install Minisign from your distribution's trusted package source
(for example `sudo apt install minisign` or `sudo dnf install minisign` when
available), or use its official installation instructions. Never install an
unknown verifier or run a downloaded shell script just to bypass a failed check.

## 2. Verify the signature with the pinned key

The Automexia v0.4.0 verification key is:

```text
RWTO3NFbh6cxrzSTATcR6SBkp/bHhwCdR48B+G7IS83pkW8XPqVDrNkN
```

Run:

```bash
minisign -Vm SHA256SUMS -x SHA256SUMS.minisig -P 'RWTO3NFbh6cxrzSTATcR6SBkp/bHhwCdR48B+G7IS83pkW8XPqVDrNkN'
```

Require a successful signature-verification message **and exit status zero**.
If it fails, stop; do not regenerate the checksum file, remove signature checks,
or substitute the key supplied by an untrusted mirror.

The [downloadable public key](https://github.com/AmjedAllaya/automexia-releases/releases/download/v0.4.0/automexia-release-key.pub)
is convenient, but downloading a key next to a package is not independent
authentication. Compare it with this pinned key through a trusted copy of this
repository. Keep a trusted copy for subsequent checks; investigate unexpected
key changes. This first-use trust still depends on GitHub/account integrity.

## 3. Verify the exact package

For an **x64 DEB**, run:

```bash
test -f automexia-terminal_0.4.0-1_amd64.deb && \
grep -Fx 'bc3df2034ccfd7bf42861f68de300e1352ee4e593fb5850abcc5396c36230566  automexia-terminal_0.4.0-1_amd64.deb' SHA256SUMS | sha256sum --check --strict -
```

Expected result:

```text
automexia-terminal_0.4.0-1_amd64.deb: OK
```

For any of the six packages, this simpler command checks all downloaded files
listed in the already authenticated checksum file:

```bash
sha256sum --check --ignore-missing SHA256SUMS
```

Require your **chosen package's exact filename followed by `OK`** as well as
exit status zero. Verification of only a guide or key file is **not** verification
of a missing package. A missing package, `FAILED`, warning, malformed line, or
nonzero exit is a stop condition. Do not install on a partial result.

## What is included?

The [release assets](https://github.com/AmjedAllaya/automexia-releases/releases/tag/v0.4.0)
include six packages and ten supporting files. The signed checksum list covers
the fourteen payload files; the checksum file and its signature are the other
two files, not self-checksumming payloads.

- `public-distribution-manifest-v1.json`: exact version, package slots and
  artifact identities.
- `automexia-terminal.spdx.json` and `automexia-terminal.cdx.json`: dependency
  inventories in SPDX and CycloneDX formats, not vulnerability-free guarantees.
- `RELEASE-NOTES.md`, `INSTALL.md`, `UNINSTALL.md`, `THIRD_PARTY_NOTICES.md`:
  version-bound notes, instructions and attributions.

GitHub's release immutability and attestation provide another integrity layer.
They do not replace the pinned-key check. The editable release-page description
and repository guides are **not** the immutable, signed guide assets. Any stale
website pointer in a v0.4.0 asset does not invalidate direct versioned downloads;
these repository guides supply the current navigation without replacing assets.

For suspected tampering, stop using the package and [report it privately](SECURITY.md).
