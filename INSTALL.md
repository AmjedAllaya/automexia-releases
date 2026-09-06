<p><img src="assets/automexia-logo.png" width="40" height="40" alt="Automexia logo"></p>

# Install Automexia on Linux

[Downloads](README.md#download-linux-v040) · [Verify first](VERIFY.md) · [Get started](GETTING-STARTED.md)

These instructions describe **v0.4.0 Linux Early Access**. Do not mix files from
different releases or architectures. Choose one installation method.

## Requirements

- A Linux desktop session, a local shell and x64 (`x86_64`) or Arm64 (`aarch64`)
  CPU. Check the architecture with `uname -m`.
- GNU/Linux system libraries: glibc, Fontconfig, FreeType, libgcc and libstdc++.
  The DEB/RPM package manager resolves declared dependencies. Portable archives
  need those libraries already installed; they are not statically linked or
  intended for Alpine/musl.
- A working desktop graphics stack. A headless SSH session is not sufficient to
  display the terminal. Do not launch the GUI with `sudo`.
- Native build and package lifecycle evidence covers **Ubuntu 22.04 x64 and
  Arm64**. The RPM was install/remove-smoke-tested on that runner, not certified
  on every Fedora-family distribution. Version-output/package checks do not
  prove every desktop, GPU or accessibility combination. Keep your existing
  terminal available during evaluation.

## 1. Download and verify

In a new empty download folder, save your package, `SHA256SUMS` and
`SHA256SUMS.minisig` from the [v0.4.0 release](https://github.com/AmjedAllaya/automexia-releases/releases/tag/v0.4.0).
Follow [the verification guide](VERIFY.md), including its pinned key and exact
package check. **Stop if any verification fails.** Then open a terminal in that
same folder and use the matching command below.

## 2A. Debian / Ubuntu: DEB

For x64:

```bash
sudo apt install ./automexia-terminal_0.4.0-1_amd64.deb
```

For Arm64:

```bash
sudo apt install ./automexia-terminal_0.4.0-1_arm64.deb
```

Review the package manager's proposed changes before accepting. If dependencies
cannot be resolved on your distribution, stop; do not force installation.

## 2B. Fedora-family systems: RPM

For x64:

```bash
sudo dnf install ./automexia-terminal-0.4.0-1.x86_64.rpm
```

For Arm64:

```bash
sudo dnf install ./automexia-terminal-0.4.0-1.aarch64.rpm
```

The release's authenticity is established by Minisign and SHA-256; this is not
a configured RPM signing-key repository. If local policy requires RPM-native
signatures or rejects the package, stop and consult your administrator. Do not
disable signature policy or use `--nodeps`/`--nogpgcheck` as a workaround.

## 2C. Portable archive

The archive has files at its root. Create a **new, empty directory** first so
extraction cannot overwrite unrelated files. `mkdir` intentionally fails if the
example directory already exists; choose a different unused name in that case.

For x64:

```bash
mkdir automexia-0.4.0-portable
tar -xzf automexia-terminal-0.4.0-x86_64-unknown-linux-gnu.tar.gz -C automexia-0.4.0-portable
```

For Arm64, use this extraction command after creating the directory:

```bash
tar -xzf automexia-terminal-0.4.0-aarch64-unknown-linux-gnu.tar.gz -C automexia-0.4.0-portable
```

Run without elevation:

```bash
./automexia-0.4.0-portable/automexia --version
./automexia-0.4.0-portable/automexia
```

Keep the executable, `shell-integration` folder, license and notices together.
The portable archive does not register a desktop launcher or automatic updater.

## 3. First launch

For an installed DEB/RPM:

```bash
automexia --version
automexia
```

The version output must include `0.4.0`. You can also use the **Automexia
Terminal** desktop application entry. If a different version launches, inspect
`command -v automexia` locally to check which installation is being used; do not
paste private paths into a public report.

Continue with [your first session](GETTING-STARTED.md). If launch fails, use
[troubleshooting](SUPPORT.md); do not change global security settings.

## Updates and rollback

There is no automatic update channel configured by these downloads. For a new
release, read its notes, verify that version's key/signature/checksums, close
Automexia, back up your configuration, and install the matching new package.
Do not reuse the v0.4.0 verification command for another release.

Keep a verified previous package and configuration backup if you need rollback.
Package managers may require an explicit downgrade operation; do not force an
incompatible dependency set. A version rollback alone does not restore settings.
For portable evaluation, keep versions in separate directories and do not run
them concurrently against the same configuration. See [removal](UNINSTALL.md).
