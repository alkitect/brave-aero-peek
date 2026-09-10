# Publish notes

Before tag: README must pass `./scripts/ci-check.sh` (required H2s + README ban tokens + Ko-fi `FUNDING.yml` / tip link + secret-file bans). See [CONTRIBUTING.md](../CONTRIBUTING.md) § README conventions.

README variant: B

First public tag: v0.2.8

**V-001 exception:** first tag equals MV3 `browser-extension/manifest.json` version (`0.2.8`), not a greenfield `0.1.0` invent. Shell metadata integer stays separate.

Default first tag is usually 0.1.0. Never copy another alkitect repo’s tag. Use `RC-BEFORE-1.0` in this file only for an intentional 0.9.x RC.

```bash
./scripts/ci-check.sh
git tag -a v0.2.8 -m "v0.2.8"
git push origin main
git push origin v0.2.8
```

Repo URL (after create): `https://github.com/alkitect/brave-aero-peek`

**Do not** ship `extension.pem` or `manifest-key.txt`.

## Human gate

**Published:** GitHub `alkitect/brave-aero-peek`, first tag `v0.2.8`.

Optional soak (does not block the tag): logout/in + `./scripts/verify-e2e.sh` scrub/corridor/header checklist.

## GitHub About

| Field | Value |
|-------|--------|
| Description | Linux Ubuntu Dock: Brave tab thumbnail strip on hover (GNOME Shell) |
| Website | _(empty — tip via README Ko-fi badge)_ |
| Topics | `linux`, `ubuntu`, `gnome`, `wayland`, `brave`, `gnome-shell-extension`, `dock` |

```bash
gh repo edit alkitect/brave-aero-peek \
  --description "Linux Ubuntu Dock: Brave tab thumbnail strip on hover (GNOME Shell)" \
  --homepage "" \
  --add-topic linux --add-topic ubuntu --add-topic gnome \
  --add-topic wayland --add-topic brave --add-topic gnome-shell-extension \
  --add-topic dock
```

Sidebar (manual if shown): Releases ✓ · Packages ✗ · Deployments ✗
