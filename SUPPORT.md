<p><img src="assets/automexia-logo.png" width="40" height="40" alt="Automexia logo"></p>

# Help with Automexia

[Downloads](README.md) · [Install](INSTALL.md) · [Verify](VERIFY.md) · [Remove](UNINSTALL.md)

## Quick troubleshooting

| Symptom | What to check |
| --- | --- |
| No download under “Latest” | Open the [v0.4.0 prerelease directly](https://github.com/AmjedAllaya/automexia-releases/releases/tag/v0.4.0). “Packages” is a separate, unused registry. |
| A website download returns 404 | Use the version-pinned [GitHub downloads](README.md#download-linux-v040). Website activation is separate from release publication. |
| Signature/checksum mismatch | Stop. Check the exact version and filenames, redownload from the official release into a new folder, and repeat [verification](VERIFY.md). Do not bypass checks. |
| `Exec format error` | Compare `uname -m` with the selected architecture. x64 and Arm64 binaries are not interchangeable. |
| Missing shared library or unresolved dependency | Use a compatible GNU/Linux distribution and its trusted package manager. Do not copy random libraries or force dependencies. Portable does not mean static. |
| A window does not open or the screen is blank | Launch from an existing terminal within a desktop session and note the redacted error. Check desktop graphics drivers through your distribution. Keep the working terminal; do not run Automexia as root. |
| Portable launch fails | Extract the verified archive into its own empty directory, retain adjacent resources, and invoke the executable with `./`. A filesystem mounted `noexec` cannot run it; use a permitted location instead of changing mount policy. |
| Another version starts | Inspect `command -v automexia` locally; a previous installation may be first on PATH. Do not overwrite an unknown executable. |
| A shortcut does something unexpected | Check the [Linux shortcut table](GETTING-STARTED.md#everyday-shortcuts), selected pane and desktop bindings. Click the intended pane before pasting. |
| Command jumping or result decorations are absent | Shell markers/integration may be unavailable. Ordinary shell output remains usable; do not assume every command or shell emits markers. |
| A font change seems ignored | Runtime font/appearance preferences can override `config.toml`. Close and reopen once, check the selected configuration root, and preserve a backup before adjustments. |

## Known limitations

v0.4.0 is Early Access. Native package checks cover Ubuntu 22.04 x64 and Arm64;
they are not a claim of complete Fedora, desktop/GPU or screen-reader testing.
Accessibility and native display behavior remain environment-dependent.

Reported behaviors still requiring exact-environment reproduction include
retained-output or decoration changes after resize, narrow-pane metadata
overlap, pointer/paste focus surprises, and dense command-palette/search UI.
These reports are not proof that every Linux setup is affected, nor are they
resolved merely because source tests pass. Preserve a safe reproduction and
avoid sensitive production work until the behavior you need is validated.

Ctrl+R / Ctrl+D have nonstandard defaults; see the [shell-key note](GETTING-STARTED.md#everyday-shortcuts).
Command markers and decorations depend on shell integration. Runtime settings
persistence covers font size and appearance, not arbitrary UI state or sessions.
No Windows, macOS or AppImage asset is available in this release.

## Report a problem safely

This archive has **Issues and Discussions disabled**. It is a download archive,
not an active public support tracker. General-support email intake is not
available in this archive. Documentation corrections can be submitted as a
small, redacted pull request here. No response-time or paid support commitment
is made here. Do not use private
vulnerability reporting for unrelated support questions.

Prepare this minimal, redacted information:

- Automexia version and exact downloaded filename.
- Distribution/version, CPU architecture, desktop session and graphics backend
  if known; do not include machine or account names.
- Shell/version, reproduction steps, expected behavior and actual behavior.
- Whether a clean shell changes the result; review any configuration excerpt.
- A minimal screenshot only after removing usernames, paths, hostnames,
  credentials, command history and organization data.

Never publish full terminal logs, environment dumps, shell profiles, private
keys or tokens. Suspected tampering, vulnerabilities or credential exposure
belong in the [private security reporting channel](SECURITY.md).
