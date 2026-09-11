# Publish notes

Before tag: README must pass `./scripts/ci-check.sh` (required H2s + README ban tokens + Ko-fi `FUNDING.yml` / tip link + secret-file bans). See [CONTRIBUTING.md](../CONTRIBUTING.md) § README conventions.

README variant: B

First public tag: v0.2.8

Current tag: v0.2.10

**Status:** **Deprecated** — successor is [alkitect/browser-aero-peek](https://github.com/alkitect/browser-aero-peek). No Wave Chromium or new browser work here.

**V-001 exception:** first tag equals MV3 `browser-extension/manifest.json` version (`0.2.8`), not a greenfield `0.1.0` invent. Shell metadata integer stays separate. After the first tag, bump MV3 + CHANGELOG, then tag (`Current tag` tracks tip).

Default first tag is usually 0.1.0. Never copy another alkitect repo’s tag. Use `RC-BEFORE-1.0` in this file only for an intentional 0.9.x RC.

```bash
./scripts/ci-check.sh
git tag -a v0.2.10 -m "v0.2.10"
git push origin main
git push origin v0.2.10
```

Repo URL: `https://github.com/alkitect/brave-aero-peek`

**Do not** ship `extension.pem` or `manifest-key.txt`.

## Human gate

**Published:** GitHub `alkitect/brave-aero-peek`, first tag `v0.2.8`, current `v0.2.10` (deprecate notice).

Optional soak (does not block the tag): logout/in + `./scripts/verify-e2e.sh` scrub/corridor/header checklist.

## GitHub About

| Field | Value |
|-------|--------|
| Description | Deprecated — use alkitect/browser-aero-peek (Brave-only Ubuntu Dock tab peek) |
| Website | _(empty — tip via README Ko-fi badge)_ |
| Topics | `linux`, `ubuntu`, `gnome`, `wayland`, `brave`, `gnome-shell-extension`, `dock`, `deprecated` |

```bash
gh repo edit alkitect/brave-aero-peek \
  --description "Deprecated — use alkitect/browser-aero-peek (Brave-only Ubuntu Dock tab peek)" \
  --homepage "" \
  --add-topic linux --add-topic ubuntu --add-topic gnome \
  --add-topic wayland --add-topic brave --add-topic gnome-shell-extension \
  --add-topic dock --add-topic deprecated
```

Sidebar (manual if shown): Releases ✓ · Packages ✗ · Deployments ✗
