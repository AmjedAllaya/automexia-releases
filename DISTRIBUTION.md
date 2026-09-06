<p><img src="assets/automexia-logo.png" width="40" height="40" alt="Automexia logo"></p>

# Distribution and trust

[Downloads](README.md) · [Verify a package](VERIFY.md) · [Security](SECURITY.md)

## What this repository contains

Automexia's public archive contains user documentation and brand assets in Git,
and versioned application packages in GitHub Releases. It does not contain the
private development workspace, signing secrets, debug symbols or private logs.
GitHub's generated source archives contain only this public metadata, not the
application source or executable.

The current release is **v0.4.0 Linux Early Access**: DEB, RPM and portable
archives for x64 and Arm64. No unpublished platform or package is implied.

## Package integrity

The complete release contains six packages and ten supporting files. A public
manifest identifies the version and artifact set; Minisign authenticates the
SHA-256 checksum list. SPDX/CycloneDX inventories and third-party notices are
provided for inspection. [Verify](VERIFY.md) before installing.

Packages are assembled and checked before publication. Once published, the
release's tag and uploaded assets are immutable. Fixes require a new version;
files are not silently replaced. The release-page description and these guides
can be updated independently and are not themselves signed release assets.

Version-specific GitHub URLs are the direct download authority here. Website
download activation is separate; a website 404 does not mean a published GitHub
prerelease is missing. `/releases/latest` is not used for this prerelease.

## Repository maintenance

The repository uses a solo-maintainer PR policy: the owner may review and merge
their own documentation PR without a second person's approval. Pull requests,
resolved discussions, signed linear history and squash merges remain required.
Force-push, default-branch deletion and rule bypasses are disallowed. Release
tags cannot be updated or deleted. This is not an independent-review claim.

Actions, Issues, Projects and Wiki are disabled in this passive archive. Private
vulnerability reporting remains available. Publication does not require a paid
CI feature in this repository.

## License and attribution

The terminal's [MIT license](LICENSE) is reproduced unchanged. Third-party
components retain their own licenses; see the version's
[THIRD_PARTY_NOTICES.md](https://github.com/AmjedAllaya/automexia-releases/releases/download/v0.4.0/THIRD_PARTY_NOTICES.md)
and package notices. Use of the Automexia name or logo does not imply endorsement
or grant additional trademark rights. Branding does not change Early Access
status or certify a package for an untested platform.
