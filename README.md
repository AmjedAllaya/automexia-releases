# Automexia Releases

This is Automexia Terminal's public, binary-only release archive. It exists so
users can download versioned packages and independently verify their identity
without exposing the private development repository.

The first public channel is Linux Early Access. A release is valid only when it
contains the complete allowlisted bundle: x64 and Arm64 DEB, RPM, and portable
archives; `SHA256SUMS`; a detached minisign signature; the public verification
key; SPDX and CycloneDX SBOMs; release notes; installation and removal guidance;
third-party notices; and the source-commit-bound public distribution manifest.

Use the stable Automexia download routes at
[automexia.com](https://www.automexia.com/) and follow the
[release trust guide](https://www.automexia.com/docs/release-trust). Do not use
automatically generated repository source archives as Automexia application
packages; they contain only this repository's public metadata.

Packages are uploaded by a least-privilege release workflow and releases become
immutable when published. Assets are never replaced under an existing version.
