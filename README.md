# Brave Aero peek

Hover Brave on the Ubuntu Dock and see your **tabs** as thumbnails — Aero-style peek for Linux.

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/alkitect/?hidefeed=true&widget=true&embed=true)

## What this does

The Ubuntu Dock already shows **window** previews when you click. It does not show **tabs** while you hover — so picking the right Brave tab still means restoring the window and hunting the tab strip.

This tool adds a hover peek: pause on the Brave dock icon and you get a strip of tab titles, favicons, and **cached** page thumbnails. Click a card to jump straight to that tab.

![Brave Aero peek on Ubuntu Dock — hover the Brave icon to see tab title and thumbnail cards](docs/images/ubuntu-dock-brave-aero-peek.png)

**Safe for click behavior:** dock **click** stays stock minimize-or-previews. Peek is hover-only. Thumbnails are from the last time that tab was on screen (Chromium cannot screenshot background tabs live).

## Who this is for

- **In:** Ubuntu 22.04 + GNOME Shell 42 **Wayland**, Ubuntu Dock, and the **Brave `.deb`**
- **In:** You keep several Brave tabs open and want to pick one from the dock without guessing
- **Not for:** Firefox; Chrome / Edge / Opera / Vivaldi; Flatpak or Snap Brave; non-GNOME desktops; replacing the global dock click-action

## Quick start

```bash
git clone https://github.com/alkitect/brave-aero-peek.git
cd brave-aero-peek
chmod +x scripts/*.sh
./scripts/install-to-local.sh --enable-automation
```

**What you installed:** the `browser-tabs-host` daemon (user unit `alkitect-browser-tabs.service`), native-messaging manifest for Brave, and Shell files for `browser-tab-dock@alkitect`. The host starts with your graphical session. You still connect Brave and enable the Shell extension yourself.

**1. Brave** — `brave://extensions` → Developer mode → Load unpacked → `browser-extension/`. Confirm the ID matches `browser-extension/extension-id.txt`. Fully quit and relaunch Brave, then run `browser-tabs-host cli list`.

**2. Shell** — Wayland needs a logout after enable:

```bash
gnome-extensions enable browser-tab-dock@alkitect
# log out and back in
```

**3. Try it** — open one Brave window with at least two tabs. Hover the Brave dock icon briefly; click a card to activate that tab. Clicking the icon itself still minimize-or-previews.

**Needs:** Ubuntu GNOME Wayland, Brave `.deb`, `systemd --user`, and a session where you can enable GNOME Shell extensions.

## Check it works

You want the hover strip to appear, a card click to focus that tab, and dock click unchanged.

```bash
./scripts/verify-host-cli.sh
./scripts/verify-dbus.sh
./scripts/verify-shell-fake.sh
# After Shell reload / logout, human checklist:
./scripts/verify-e2e.sh
```

- If `cli list` says no extension: reload the unpacked add-on, quit Brave fully, relaunch, try again.
- If hover does nothing after enable: confirm Wayland logout/in, then that `browser-tab-dock@alkitect` is enabled.

Maintainers: `./scripts/ci-check.sh`.

## Uninstall

```bash
./scripts/uninstall-from-local.sh
```

Remove the add-on in `brave://extensions` if you loaded it unpacked. That step is manual.

## How it works

Three small pieces share tab state with the dock:

| Piece | Role |
|-------|------|
| Brave MV3 add-on | Lists / activates tabs; inlines favicons; caches visible-tab PNG thumbs |
| `browser-tabs-host` | Native messaging ↔ session D-Bus |
| Shell extension | Hover dwell on the Ubuntu Dock → peek strip; raise the window after Activate |

Installed names: `browser-tabs-host`, `alkitect-browser-tabs.service`, Shell uuid `browser-tab-dock@alkitect`, Brave add-on “Alkitect Browser Tab Dock”.

Versions: MV3 `browser-extension/manifest.json` (git tags track this) · Shell `metadata.json` integer (GNOME scheme). Deeper reading: [ARCHITECTURE](docs/ARCHITECTURE.md) · [ADR-001](docs/architecture/ADR-001-ipc-and-dock-intercept.md) · [SECURITY](docs/SECURITY.md).

## Limits & safety

- **Linux + Ubuntu Dock + Brave `.deb` only** — other OSes, docks, and browsers are unsupported.
- **One Brave window** with ≥2 tabs for peek; several Brave windows → no tab strip (stock window previews still work).
- **Thumbnails are page screenshots** (more sensitive than titles). Same-UID processes on D-Bus or the host socket can read them — details in [SECURITY.md](docs/SECURITY.md).
- Hover dwell and host rate limits reduce spam while scrubbing past the icon.
- This GitHub repo is the **release source** for tagged releases and public docs — see [CONTRIBUTING.md](CONTRIBUTING.md).

## License

GPL-3.0-only — see [LICENSE](LICENSE).

Copyright (C) 2026 alkitect

Optional tip jar: [ko-fi.com/alkitect](https://ko-fi.com/alkitect/?hidefeed=true&widget=true&embed=true)
