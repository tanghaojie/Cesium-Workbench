---
title: Standalone Cesium Workbench product icon adoption
status: completed
date: 2026-11-18
---

# Standalone Cesium Workbench product icon adoption

## Goal and confirmed scope

Replace legacy template and Cyber-Sight brand icons in Cesium-Workbench with the standalone "Cesium 三维工作台" product icon (`v1/products/standalone_cesium_gis.svg` from the JTLab IP design system), commit and push on a topic branch, and publish through CI-gated PR auto-merge, organization source synchronization and GitHub Pages deployment.

## Completed implementation

- [x] Verified an empty Git staging area and clean worktree on `master` (`40071ac61c74e52223b9b178a71a5f4e282db5be`), preserved branch/tag `1.0.0`, and created `feat/brand-icon`.
- [x] Updated active Geo (`docs/design/geo-workbench.md`) and search-discovery (`docs/design/search-discovery.md`, `docs/guides/search-discovery.md`) records.
- [x] Added `public/favicon.svg`, multi-resolution 32-bit RGBA `public/favicon.ico` (`16x16`, `32x32`, `48x48`) and `public/apple-touch-icon.png` (`180x180`) rendered from `standalone_cesium_gis.svg`.
- [x] Linked `/favicon.ico`, `/favicon.svg` and `/apple-touch-icon.png` in `index.html`, `geo.html`, `public/about/index.html` and `public/about/en/index.html`; replaced the placeholder `CW` masthead badge on `/about/` and `/about/en/` with `/favicon.svg`.
- [x] Replaced the source brand mark in `src/shared/components/AppLogo.vue` with instance-scoped SVG definitions (`useId`) of the standalone Cesium Workbench mark, adjusted `GeoLoadState.vue` framing, added the product icon header to `README.md` / `README.en.md`, and updated `NOTICE` attribution.
- [x] Completed local engineering and static `dist` checks; archived this plan and AI log before publishing the PR.

## Actual validation

- Windows, Node `v24.19.0`, pnpm `11.22.0`.
- `pnpm install --frozen-lockfile`: passed with zero lockfile or dependency changes.
- `pnpm format` and `pnpm format:check`: passed.
- `pnpm lint`: passed.
- `pnpm build` (`vue-tsc --noEmit && tsc -p tsconfig.node.json --noEmit && vite build`): passed; existing Dart Sass legacy JS API and bundle-size advisories remain unchanged.
- Static `dist` inspection: confirmed `dist/favicon.svg`, multi-frame `dist/favicon.ico` (`16x16`, `32x32`, `48x48`), `dist/apple-touch-icon.png` (`180x180`), icon `<link>` tags and valid JSON-LD across all four HTML documents, `/favicon.svg` masthead mark in both `/about/` pages, and intact `cesiumStatic` output.
- `git diff --check`: passed. No frontend unit, component, E2E or browser automation was created or run.

## Delivery and pending human acceptance

Delivery publishes `feat/brand-icon`, opens a pull request to `tanghaojie/Cesium-Workbench` `master`, enables exact-SHA CI-gated auto-merge under `docs/design/automatic-delivery.md`, and inspects required `verify` CI, `Sync source to organization`, `Deploy GitHub Pages` and live HTTP responses after push; no pre-push remote workflow success is claimed in this file. Browser tab rendering across themes/OSes, `/about/` visual layout and `GeoLoadState` presentation remain pending human visual/browser acceptance.
