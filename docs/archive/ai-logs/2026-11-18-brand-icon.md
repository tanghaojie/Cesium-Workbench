---
title: Standalone Cesium Workbench product icon adoption
status: completed
date: 2026-11-18
change_type: feat
---

# Standalone Cesium Workbench product icon adoption

## User goal and IP design selection

The owner asked to update Cesium-Workbench's icon to the "Cesium 三维工作台" icon from `桀士IP设计`, commit and push the code, and publish live. Under the dual-brand architecture in `桀士IP设计/v1/设计规范总览.md` and `v1/模块化产品家族看板.html`, `v1/products/standalone_cesium_gis.svg` (`-24°` sunlit 3D Earth `#338AAF`, continuous titanium-gold geodesic orbit, telemetry satellite node and four GIS reticles) is defined for standalone product deployment (website favicon, Apple Touch/PWA icon, WebGIS entry and standalone GitHub repository), whereas `product_cesium_gis.svg` is reserved for parent-brand ecosystem matrices.

## Baseline and boundaries

Staging and worktree were clean on `master` (`40071ac61c74e52223b9b178a71a5f4e282db5be`). Branch `1.0.0` (`fcea9e53485f356f96fb64cf6cd692f77513d6bd`) and tag `1.0.0` remain preserved. Created topic branch `feat/brand-icon` after reading `docs/README.md`, `docs/design/geo-workbench.md`, `docs/design/organization-publication.md`, `docs/design/search-discovery.md` and `docs/design/automatic-delivery.md`. No secrets were read or recorded, and no runtime Viewer, clock, plugin or capture contracts changed.

## Actual changes

- Generated `public/favicon.svg` (200 × 200 vector), `public/favicon.ico` (32-bit RGBA `16x16`, `32x32`, `48x48` DIB entries) and `public/apple-touch-icon.png` (`180x180` RGBA PNG) from `standalone_cesium_gis.svg` via `resvg`, visually verifying rendered gradients, orbital occlusion and alpha channels.
- Updated `index.html`, `geo.html`, `public/about/index.html` and `public/about/en/index.html` icon links; replaced the placeholder `CW` circle in both `/about/` mastheads with `/favicon.svg` and updated `.brand-mark` in `public/about/about.css`.
- Replaced the Cyber-Sight mark in `src/shared/components/AppLogo.vue` with instance-scoped SVG definitions (`useId`) of the standalone Cesium Workbench mark, adjusted `.geo-load-state__mark` sizing in `src/modules/geo/components/shell/GeoLoadState.vue`, added the product icon above the headings in `README.md` and `README.en.md`, and updated `NOTICE` attribution.
- Updated active design/guide docs and documentation indexes. No `package.json` or `pnpm-lock.yaml` dependency changes were needed.

## Actual verification

On Windows with Node `v24.19.0` and pnpm `11.22.0`, `pnpm install --frozen-lockfile`, `pnpm format`, `pnpm format:check`, `pnpm lint` and `pnpm build` (including `vue-tsc` and `tsconfig.node.json` typechecks) all passed. Static `dist` verification confirmed all emitted icon files, `<link rel="icon">` / `<link rel="apple-touch-icon">` declarations, `/about/` masthead `<img src="/favicon.svg">` tags, valid JSON-LD and intact `cesiumStatic` assets. `git diff --check` passed. No frontend or browser automation was created or run.

## Delivery and pending acceptance

Associated commit: `feat(brand): adopt standalone Cesium Workbench IP icon` with the actual `Gemini 4 Carbon` co-author trailer. Topic PR creation, exact-head CI-gated auto-merge opt-in, required `verify` check, personal-to-organization source synchronization, GitHub Pages deployment and live HTTP checks are executed and reported after push; their completion is not claimed prior to push. Visual browser rendering across themes/DPIs and interactive workspace acceptance remain with the owner.
