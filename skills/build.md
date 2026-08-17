# Phase 3: Build

## Steps

1. Copy `assets/template.html` → `index.html`
2. Fill `HOTEL` object and `DAYS` array with structured data from Phase 1 + 2
3. Each location needs: `name`, `lat/lng`, `type`, `time`, `desc`; optional: `budget`, `detail`, `pay`, `xhs`, `reserve`, `gmap`
4. Fill `overviewContent()` with trip summary and payment warnings

## Location types

`food` | `spot` | `drink` | `hotel` | `transport`

## Payment chip values

`1` = confirmed yes (green)  `0.5` = maybe (orange)  omit = not shown

## Design system (optional)

Default template uses Apple style (SF Pro, light theme, frosted glass).

To switch styles, grab a `DESIGN.md` from [awesome-design-md](https://github.com/VoltAgent/awesome-design-md):

```bash
curl -O https://raw.githubusercontent.com/VoltAgent/awesome-design-md/main/design-md/<brand>/DESIGN.md
```

Then adjust `:root` CSS variables in `template.html` (colors, fonts, spacing, border-radius).

## Deploy (optional)

```bash
git init && git add . && git commit -m "trip map"
gh repo create REPO --public --source=. --push
# Import from vercel.com/new — auto-deploys on push
```
