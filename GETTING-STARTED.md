<p><img src="assets/automexia-logo.png" width="40" height="40" alt="Automexia logo"></p>

# Make yourself at home

[Downloads](README.md) · [Install](INSTALL.md) · [Troubleshooting](SUPPORT.md)

These are the default **Linux v0.4.0** controls. Custom bindings or a desktop
shortcut may change what reaches the application. Automexia hosts your shell;
the shell still owns its commands, history, quoting and jobs.

## Your first session

Launch `automexia` from an existing terminal or select **Automexia Terminal** in
the desktop application menu. Type a harmless command such as `pwd` and press
Enter. Wait for the window and shell prompt before using shortcuts.

Open a tab with **Ctrl+T**, or a fresh split with **Ctrl+Shift+R** (right) or
**Ctrl+Shift+D** (down). Click a pane before typing or pasting into it. Each pane
has its own shell; closing one can stop the process running inside it.

## Everyday shortcuts

| Do this | Default shortcut |
| --- | --- |
| Discover actions in the command palette | Ctrl+Shift+P |
| New window tab | Ctrl+T |
| New tab in the selected pane | Ctrl+Shift+T |
| Next / previous window tab | Ctrl+Tab / Ctrl+Shift+Tab |
| Next / previous pane-local tab | Alt+PageDown / Alt+PageUp |
| Fresh split right / down | Ctrl+Shift+R / Ctrl+Shift+D |
| Focus a neighboring pane | Alt+Arrow |
| Close the focused pane/tab | Ctrl+Shift+W |
| Copy selection / paste clipboard | Ctrl+Shift+C / Ctrl+Shift+V |
| Find in selected pane / all visible panes | Ctrl+F / Ctrl+Shift+F |
| Previous / next marked command | Ctrl+Shift+Up / Ctrl+Shift+Down |
| Increase / decrease font size | Ctrl+= / Ctrl+- |
| Reset font size | Ctrl+0 |
| Switch light / dark appearance | Alt+Shift+T |
| Open configuration | Ctrl+Shift+, |

**Shell-key compatibility:** Ctrl+R and Ctrl+D currently clone a split instead
of forwarding the usual shell controls. Use **Ctrl+Alt+R** for shell reverse
history search and **Ctrl+Alt+D** for EOF, or review your keybinding profile.
Ctrl+C copies when text is selected; without a selection it is available to
interrupt the shell command. Clipboard text is untrusted: review it before
pressing Enter, especially multiline text.

## Find without losing your place

Press Ctrl+F, enter text, then Enter / Shift+Enter for next / previous matches.
Ctrl+Shift+F changes the same query to all **visible panes**; Ctrl+F switches
back to the selected pane. It is not filesystem search or a search across other
window tabs. Esc closes search. Command-jump navigation requires shell command
markers; arbitrary output or shells without integration do not provide them.

## Settings that stay with you

Runtime font size and appearance changes are saved for the next launch. This
does **not** mean every transient UI control or open session is persisted.

On Linux the normal configuration root is `$XDG_CONFIG_HOME/automexia`, or
`~/.config/automexia` if XDG_CONFIG_HOME is unset. An explicit
`AUTOMEXIA_CONFIG_HOME` overrides that root. These are location templates, not
paths to copy into a public report.

Create starter configuration without overwriting an existing file:

```bash
automexia --write-config
```

Use Ctrl+Shift+, to open the configuration, or edit `config.toml` in that root.
Back it up before editing. For example, these keys adjust basic appearance:

```toml
line-height = 1.22
confirm-before-quit = true

[fonts]
size = 16.0
```

Runtime appearance preferences are stored separately in
`state/user-preferences-v1.toml` and can override font/appearance values in
`config.toml`. Do not edit that state file while Automexia is running. Invalid
runtime configuration reloads preserve the last working configuration; correct
the reported setting instead of deleting the whole configuration directory.

## Launch options

```bash
automexia --help
automexia --version
automexia --working-dir ./project
automexia -e bash --noprofile --norc
```

The working directory must exist. `-e` must be the final Automexia option:
everything following the executable is passed to that program as arguments.
Pipelines and redirects belong inside the shell, not in a quoted executable
string. The Bash example opens a clean shell; it does not edit your dotfiles.

For portable installation, use the extracted executable's relative path instead
of `automexia`. For help with missing shell decorations, rendering or input,
see [known limitations and troubleshooting](SUPPORT.md).
