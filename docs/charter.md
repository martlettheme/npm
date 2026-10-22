# Martlet design charter

Draft 0.1 for review · October 21, 2026

This charter proposes the direction for Martlet's development as a complete design system. Its starting observation is agreed: Martlet feels warming, even within its blue, white, and gold vocabulary. The principles below translate that observation into criteria for design and review. Existing package contracts remain in force; this document introduces no token, API, or compatibility changes and does not imply that the proposed component inventory has shipped.

## Purpose and character

Martlet should make substantial digital experiences feel welcoming, readable, and considered. Its warmth comes from typography, proportion, grouping, and the way an interface helps someone proceed. That character must remain apparent when the interface contains a long document, a complicated form, or an unfamiliar error.

The existing Cambo prose, Lato interface text, selective Cinzel display roles, and restrained use of gold provide a starting vocabulary. Warmth does not prescribe a particular hue or require a decorative treatment on every page. It should persist in Light and Dark modes and in ordinary working components.

Martlet's initial applications supply useful examples, but its scope includes publishing, services, collections, and interactive applications. An article and a dashboard should both be recognizably Martlet. Content, organization, and personal identity belong to the adopting project.

## Design principles

**Make reading comfortable.** Establish a clear sequence through titles, introductions, body text, supporting information, and actions. Type roles, reading measure, line spacing, and paragraph rhythm should help people sustain attention. Navigation, labels, metadata, and numerical information retain the typography best suited to their tasks.

**Use proximity to establish relationships.** A label, its control, and its help or error message form one understandable group. Separate the next group more clearly. Apply the same reasoning to cards, annotations, toolbars, and document sections. A spacing scale needs semantic rules explaining which relationships its values express.

**Let hierarchy carry the composition.** Use typographic differences, alignment, proportion, and selective rules to establish importance. Borders, surfaces, and accents should have identifiable purposes. A page must remain understandable when a decorative image or brand mark is absent.

**Guide actions with clear language.** Explain what an action does and what information a person needs to provide. Integrate useful assistance into the task, and keep labels and consequences explicit. Warmth must remain compatible with precise validation, urgent warnings, and unmistakable destructive actions.

**Preserve continuity during change.** Loading, expansion, validation, and navigation should leave people able to understand where they are. Motion should explain a change in state or position. Respect reduced-motion preferences and maintain understandable feedback when animation is absent.

## Foundations and component contracts

The specification should cover semantic color, typography, spacing, reading and content widths, responsive composition, density, borders, shape, elevation, layering, and motion. Distinguish reference scales from semantic decisions such as field spacing, panel padding, and section separation. Numerical values and public token names belong in versioned specifications; this charter provides the criteria for choosing them.

The component inventory should expand through forms, navigation, feedback, disclosure, overlays, data presentation, and complete task patterns. Each supported component needs a stated purpose, anatomy, applicable states, interaction rules, content guidance, responsive behavior, and accessibility acceptance criteria. Include examples of how components work together. Record planned, experimental, and stable capabilities clearly.

Accessibility is a condition of acceptance. Review keyboard operation, focus visibility and restoration, labels and announcements, contrast, text enlargement, reflow, forced colors, and reduced motion where applicable. Support long content, localization, and changes in reading direction. Define what remains available without JavaScript and identify interactions that require it. Visual character cannot justify a loss of function.

## Relationship with Krigsvold

Martlet and Krigsvold share a vocabulary of blue, white, gold, order, and restraint. Their different emotional temperatures emerged through their development. Neither system should be designed by mechanically reversing the other's decisions. Both can reach the same answer when that answer serves the user.

Share interaction contracts, accessibility work, testing, and tooling where practical. Preserve independent decisions about typography, composition, surfaces, rhythm, and emphasis. Martlet's distinction must be visible in ordinary components and complete experiences, beyond a palette swap. Neither family has exclusive ownership of editorial or institutional applications.

## Evidence and review

The next milestone is four comparative experiences: an article with supporting material, a substantial form, a searchable collection, and an application dashboard. Use the same content and functionality in both families. Review whether Martlet's warmth remains apparent with brand marks removed, whether the hierarchy is clear, and whether the experience works at narrow widths and with enlarged text. Typography, grouping, and composition should provide evidence of its character.

Use the live sites as consumers and test cases. Reusable decisions belong in the packages and specifications; site navigation, brand assets, routing, content, analytics, and consent policy remain host responsibilities. Examples embedded in a host site should inherit that site's shared page shell. Standalone starters should identify their purpose explicitly.

Maintainers should record the reasons for consequential changes and identify which decisions remain provisional. A review should connect a proposal to this charter, to a demonstrated user need, and to its compatibility implications. Version and deprecate stable contracts deliberately. Revise the charter when experience supports a better account of Martlet's character.
