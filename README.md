# Martlet core

`@martlet/theme` is the framework-independent source of truth for Martlet. It contains Light/Dark semantic colors and the typography, spacing, shape, depth, and interaction definitions extracted from jameshoward.us.

## Design direction

For the proposed design direction and criteria for expanding the system, read the [Martlet design charter](docs/charter.md).

## Choose what to adopt

| Import | Effect |
| --- | --- |
| `@martlet/theme/css` | Original scoped Light/Dark color variables only; unchanged from v1 |
| `@martlet/theme/foundation.css` | Namespaced design variables; no font loading or element styles |
| `@martlet/theme/typography.css` | Text roles inside `.martlet`; requires foundation variables |
| `@martlet/theme/fonts.css` | Optional, locally bundled Cambo, Lato, Cinzel, and IBM Plex Mono assets through Fontsource |
| `@martlet/theme/components.css` | Optional namespaced interface primitives; requires colors and foundation |
| `@martlet/theme/full.css` | Colors, foundation, typography, and components; fonts remain optional |
| `@martlet/theme/legacy.css` | Optional variable aliases for incremental website migration |

```js
import '@martlet/theme/full.css';
import '@martlet/theme/fonts.css';
import { light, dark, foundation, design, capabilities } from '@martlet/theme';
```

Set `data-martlet="light"` or `data-martlet="dark"` on the element to theme; add `class="martlet"` to opt into typography and interface styling. Modes may coexist on the same page. CSS remains available without JavaScript; font package imports require a CSS-capable bundler. ESM and CommonJS exports, TypeScript declarations, per-mode JSON, `tokens.json`, `foundation.json`, `design.json`, `capabilities.json`, and highlight.js styles are explicit package exports.

## Typography and overrides

- Serif: Cambo, for prose and primary headings.
- Sans: Lato, for interface text, navigation, and metadata.
- Display: Cinzel, for display accents and secondary heading roles.
- Monospace: IBM Plex Mono, for code and terminal text.

These roles come from the originating personal site, not the demonstration site's former Space Grotesk/DM Sans pairing. Berkeley Mono is not distributed. An owner who has licensed it can override `--martlet-font-mono` on their own root or theme scope. Generic consumers need no proprietary fonts. See NOTICE.md for font licenses.

The optional full stylesheet is not a site template: it includes no personal identity, content, analytics, or consent policy. See [`@martlet/astro`](https://github.com/martlettheme/astro) for Astro composition and a neutral starter.

## Source and releases

Edit `source.json` here; run `npm ci --ignore-scripts`, `npm run build`, `npm test`, and `npm pack`. Generated `dist/` is committed for review and reproducibility. Fontsource dependencies are pinned; lockfiles retain their integrity. The source website's original colors are retained as separate identity tokens rather than silently replacing existing semantic app colors. Reduced-motion preferences zero the shared motion tokens.

The `capabilities` export records what each integration applies, requires separate configuration for, or cannot support. A browser color theme does not change fonts. Editors and terminals use the monospace role only where their host allows it.

The npm scope is `martlet`. Install the published core with `npm install @martlet/theme`. Package versions are independent of application-port versions.

Application port generators in `martlettheme/martlettheme` consume this package. They must not regenerate it. CI never publishes automatically.

## Layouts

Version 2.1 adds optional [`layout.css`](docs/layout.md), the `layout` JavaScript export, and `layout.json`. Layout primitives cover containers, vertical stacks, wrapping clusters, bounded grids, sidebars, and paired regions. Import `@martlet/theme/full.css` for the complete styling layer or add `@martlet/theme/layout.css` after `foundation.css` for structural classes alone. See [source observations and responsive rules](docs/layout.md).

## Releases

Stable GitHub releases can publish automatically through npm trusted publishing. See [release setup](docs/releasing.md) for the one-time package authorization and release order.
