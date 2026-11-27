# Terminal tab counts (taskbar add-on)

Lets the [Taskbar](../taskbar/README.md) show how many tabs each COSMIC Terminal window has, for
example "3 tabs" under the window title.

COSMIC Terminal does not tell other programs about its tabs. This add-on installs a COSMIC
Terminal with one small addition: it writes its window titles and tab counts to a file the
taskbar reads. Everything else is the normal COSMIC Terminal, built from System76's source at the
version the patches were tested on.

It also has an optional **copy on select**: text you select with the mouse goes straight to the
clipboard, ready for Ctrl+V anywhere. Only selections in the terminal are copied, so Ctrl+A in a
browser field never overwrites your clipboard.

The tab counts are only useful together with the Taskbar.

## Install

```sh
./install.sh terminal-tabs
```

Needs Rust and a few build packages (the installer offers to install them). Afterwards, close
and reopen open terminal windows: only terminals started after the install show a count.

## Uninstall

```sh
./install.sh --uninstall terminal-tabs
```

Super+T, the launcher and the dock start COSMIC's own terminal again.

## Settings

**Copy on select** (off by default). Turn it on:

```sh
mkdir -p ~/.config/term-tabs && touch ~/.config/term-tabs/copy-on-select
```

Turn it off: `rm ~/.config/term-tabs/copy-on-select`. Both take effect at once, also in open
terminals started after the install. Middle-click paste works as before either way.

## Known limits

- Tabs of split panes are added up.
- Two terminal windows with exactly the same title get no count.
- A COSMIC update needs no rebuild: it is always built from the tested version. `./install.sh --update`
  brings new releases, which move the patches to newer COSMIC versions.

Technical details: [docs/terminal-tabs.md](../docs/terminal-tabs.md).
