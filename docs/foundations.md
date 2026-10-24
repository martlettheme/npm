# Martlet foundations specification

Version 0.1 · Working specification · October 21, 2026

The [adopted charter](charter.md) governs this specification. The values below describe the shipped `@martlet/theme` 2.1.0 foundation and layout contracts. Normative requirements describe what new components must satisfy; they do not certify existing components. Application-specific experiments must remain identifiable until real usage validates them.

## Character and hierarchy

Martlet makes substantial work feel welcoming. Cambo gives reading and headings a human rhythm; Lato keeps controls legible. Use introductions, related groups, generous vertical rhythm, and selective gold accents to orient a person before asking for action. Cinzel belongs to occasional display accents, never every field label.

A page identifies its purpose, then its primary task, then supporting information. Use one main landmark and a descriptive h1. Related controls form a group with a visible heading or legend. Put explanations close to the decisions they explain. Do not communicate hierarchy, selection, validation, or maturity through color alone.

## Shipped measurements

All CSS properties carry the `--martlet-` prefix. Numbers in spacing token names are family-local identifiers, not interchangeable units. In particular, `space-3` differs between Martlet and Krigsvold. Cross-family components use semantic relationships and family adapters rather than copying numeric token names.

| Token | Shipped value |
| --- | --- |
| `space-1` | `.25rem` |
| `space-2` | `.5rem` |
| `space-3` | `1rem` |
| `space-4` | `1.5rem` |
| `space-5` | `2.5rem` |
| `space-6` | `4rem` |
| `space-7` | `6rem` |
| `space-8` | `8rem` |
| `reading-width` | `48rem` |
| `content-width` | `78rem` |
| `archive-width` | `88rem` |
| `text-body` | `1.075rem` |
| `text-h1` | `clamp(2.25rem, 5vw, 4.65rem)` |
| `text-h2` | `clamp(1.75rem, 3vw, 2.6rem)` |
| `text-h3` | `clamp(1.25rem, 2vw, 1.65rem)` |
| `leading-body` | `1.72` |
| `leading-heading` | `1.18` |
| `radius-control` | `0` |
| `radius-card` | `0` |
| `focus-width` | `3px` |
| `focus-gap` | `3px` |
| `gutter` | `clamp(1rem, 3vw, 2rem)` |
| `control-height` | `2.8rem` |
| `control-padding` | `.65rem .8rem` |
| `button-padding` | `.65rem 1.1rem` |
| `motion-duration` | `.2s` |
| `layout-gap` | `1.5rem` |
| `layout-gap-small` | `.75rem` |
| `layout-gap-large` | `2.5rem` |
| `layout-sidebar-width` | `16rem` |
| `layout-main-min` | `30rem` |
| `layout-grid-min` | `18rem` |
| `layout-split-min` | `20rem` |
| `layout-section-space` | `clamp(3rem, 6vw, 6rem)` |

The complete [foundation JSON](../dist/foundation.json) and [layout contract](../dist/layout.json) remain the machine-readable sources for shipped values. Typography roles are Cambo/Lato/Cinzel/IBM Plex Mono for Martlet and Roboto/Roboto Slab/Roboto Mono for Krigsvold. A missing font must leave the page readable using the supplied fallback stacks. Font loading must not hide controls or critical instructions.

## Spacing relationships

Use small layout spacing inside a related group, regular spacing between sibling groups, and large spacing between distinct tasks. Public reading pages use the shipped section spacing; an application does not inherit a public hero's vertical padding merely because it has a title. Margins on content must not double the parent's layout gap. A nested layout establishes its own spacing context.

The initial React workbench proposes `field-gap`, `group-gap`, `region-gap`, `page-gutter`, and `row-padding` as application roles. These aliases live in the experimental React styles, not in the stable theme contract. Measure the distinction between fields, groups, and regions during real registry work before promoting them. Never compress an interface simply to fit more rows.

## Responsive composition

Containers are bounded by reading, content, or archive measure. Layout primitives wrap according to their content minima: grids use their minimum cell size; sidebar and split regions wrap without changing source order. The smallest viewport must have one coherent reading and focus order. Breakpoints are consequences of content, not device names.

At 320 CSS pixels and at 400% zoom on a 1280-pixel viewport, navigation wraps, forms become one column, and action groups wrap. Long identifiers and translated copy cannot force page-wide overflow. A genuinely two-dimensional table may scroll inside a labelled, keyboard-focusable region. Keep captions, selection controls, and row actions discoverable. Do not remove columns solely to conceal overflow.

## Type and density

Use the documented font roles and unitless line heights. Application fields, tables, and navigation use the sans family. Preserve a clear heading-to-body hierarchy without applying public hero sizes to an editor panel. Text must remain usable at 200% resizing and with user text-spacing overrides. Labels remain visible when a field contains a value.

This specification recognizes comfortable density only. Compact density is proposed and requires a real high-volume task before adoption. Control hit areas remain at least 44 by 44 CSS pixels in the new React implementation. A denser row changes padding and hierarchy, never silently shrinks interaction targets or body text. Existing smaller legacy controls need review rather than retrospective certification.

## Surfaces and layering

Use semantic canvas, subtle, sunken, and overlay colors from the theme. Flat surfaces and rules establish most structure. Shadow tokens exist but do not justify elevating every section. Overlay content requires a backdrop, an accessible name, and an explicit dismissal path.

Proposed application layers are base 0, sticky context 10, and transient non-modal feedback 20. Native modal dialogs use the browser top layer and must not depend on a fabricated large z-index. Sticky regions may not obscure focused controls or error summaries. Avoid sticky layout on small screens unless it remains usable at zoom.

## Motion

Use the shipped duration and easing for brief state changes. Motion communicates a change; it must not delay submitting, saving, navigating, or reading feedback. With `prefers-reduced-motion: reduce`, remove nonessential transitions, smooth scrolling, and decorative animation. Never require animation to understand a saved or failed state. Loading and saving states include text and remain announced without repeated alerts.

## Accessibility and interaction contracts

Target WCAG 2.2 AA. Verify normal text contrast of 4.5:1, large text 3:1, and essential control boundaries and focus indicators 3:1 against adjacent colors. Measure actual combinations in both light and dark modes. Tokens alone cannot certify a composition. Retain a visible focus ring, logical keyboard order, a skip link, native form semantics, and meaningful names.

Validation associates field errors with controls, marks invalid controls, and offers an error summary that can receive focus. Keep entered values after failure. Announce successful saves with a polite status; use an alert for blocking failures. A modal traps focus through native dialog behavior, supports Escape, and returns focus to its trigger. Disabled and read-only are distinct states. Loading, empty, no-match, invalid, unavailable, saving, saved, failed, conflict, and unsaved-navigation states must be explicitly designed.

## Evidence and change control

The live baseline is https://jameshoward.us/. It supplies evidence for publishing and public navigation. The [design workbench](https://github.com/howardjp/design-workbench) supplies an experimental administration consumer. Its existence is not proof of sustained use or complete accessibility. Record the task, observed failure, proposed change, tests, and result in real use. Replace an inherited decision when generalization fails, then update the original site and verify the result there.

Before a foundation becomes stable, document its consumers, browser and assistive-technology coverage, responsive and contrast checks, migration impact, and acceptance criteria. Review same-content article, substantial form, searchable collection, and dashboard experiences across both families. Promote aliases only after evidence; version public changes and publish migrations. The current React packages and workbench remain experimental. The construction plan and registry contract describe the remaining work.

## Source reconciliation and consolidation

The October 23 source audit refines this working specification. Use [source decisions](source-decisions.md) for observed objects, [grammar](grammar.md) for experimental application relationships, and [consolidation](consolidation.md) for opt-in profiles and framework support. The shipped 2.1.0 measurements above are historical baseline values, not proof that all defaults match the observed source cascade. The 2.2.0 candidate adds opt-in relationship aliases without promoting them to stable foundation requirements.
