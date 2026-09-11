# Changelog

## Unreleased

## 0.2.10

- Deprecated: Brave-only lane is frozen. README banner and Related point new installs to [alkitect/browser-aero-peek](https://github.com/alkitect/browser-aero-peek).
- Docs: Who-this-is-for / Quick start warn that this tree is rollback/history only.
- CI: under `ALKITECT_CI_TMP`, `verify-host-cli` uses a private D-Bus so a live multi-browser host cannot break unscoped `cli list`.

## 0.2.9

- MV3 / Shell: drop “Alkitect” from display names; credit `alkitect` as author in metadata/description (Shell `author` field + description).
- Shell metadata integer 10 (author/description metadata).
- README: humanize flow (problem → peek → screenshot; Quick start as numbered story).
- README: Ubuntu Dock hover screenshot under **What this does**.
- README: Related + Install clash notes for the multi-browser daily-driver lane.

## 0.2.8

- Hover dwell peek strip on Ubuntu Dock for Brave (favicon + title above cached PNG thumbs).
- MV3: inline favicons, `captureVisibleTab` thumb cache, native messaging bridge.
- Host: session D-Bus + Unix socket; systemd `WantedBy=graphical-session.target`.
- Shell metadata integer 9: soft dwell, leave corridor, card header, empty “No preview yet”.
- First public extract scaffolding (GPL-3.0-only).
