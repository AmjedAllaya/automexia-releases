<p><img src="assets/automexia-logo.png" width="40" height="40" alt="Automexia logo"></p>

# Remove Automexia

[Downloads](README.md) · [Install](INSTALL.md) · [Help](SUPPORT.md)

Finish or stop work in every Automexia pane, then close all Automexia windows.
Use another terminal to remove the package. Choose the method you installed.

## Debian / Ubuntu

```bash
sudo apt remove automexia-terminal
```

## Fedora-family systems

```bash
sudo dnf remove automexia-terminal
```

Review the package manager's proposed removals before accepting. Do not use a
broad autoremove or erase unrelated packages simply to remove Automexia.

## Portable archive

After closing its process, remove **only the exact extraction directory you
created** using your file manager. Confirm it contains that portable copy, not
projects or unrelated files. Remove a launcher/symlink only if you created it
for that same copy. No wildcard or recursive shell deletion is required.

## Your settings and shell

Package removal does not intentionally delete personal configuration. Keep it
for reinstallation or back it up before separately removing Automexia's exact
configuration directory. See [configuration locations](GETTING-STARTED.md#settings-that-stay-with-you).
Never delete a whole home, `.config` or shell-profile directory.

Normal launch uses session-local shell integration. If you separately installed
persistent integration, inspect `automexia shell-integration doctor` and run
`automexia shell-integration uninstall` **before removing the executable**, only
when you intend to remove Automexia-owned integration. This is not permission to
delete custom shell profiles. Review diagnostics locally and redact them before
sharing.

After removal, the packaged executable should no longer be installed. If
`command -v automexia` still finds something, inspect which other installation
owns it rather than deleting it automatically. Running shell commands, history,
projects and files outside Automexia's own package remain yours.
