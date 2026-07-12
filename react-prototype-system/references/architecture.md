# Architecture and Placement

Use a layered dependency model without forcing a new folder taxonomy onto a coherent existing repository.

## Contents

- [Dependency Direction](#dependency-direction)
- [Existing Repository First](#existing-repository-first)
- [Greenfield Baseline](#greenfield-baseline)
- [Placement Decisions](#placement-decisions)
- [Screen Rule](#screen-rule)
- [Extraction Rule](#extraction-rule)
- [Boundary Rule](#boundary-rule)
- [Prototype Versus Production](#prototype-versus-production)

## Dependency Direction

Use this conceptual order:

`tokens -> primitives -> patterns -> layouts -> screens -> flows`

Higher layers may import lower layers. Lower layers must not import higher layers.

Keep supporting concerns beside this hierarchy:

- hooks or controllers own reusable behavior
- services or adapters own external side effects
- mocks own prototype data and deterministic responses
- types own shared domain contracts when no closer owner is better
- utilities own pure, domain-neutral transformations

## Existing Repository First

Before adding folders:

1. Locate existing route, feature, component, styling, and test conventions.
2. Find the nearest analogous feature.
3. Extend the established ownership boundary.
4. Add a new layer only when the repository lacks a clear home.

Do not rename or relocate unrelated code to make it resemble this reference.

## Greenfield Baseline

Use this only when no stronger project convention exists:

Default source files to TypeScript (`.ts` and `.tsx`) and use Tailwind CSS for component styling and responsive behavior.

```text
src/
  app/                 # app setup, providers, router, global shell
  components/
    ui/                # product-neutral primitives
    app/               # reusable product/domain patterns
  layouts/             # structural composition shared by screens
  pages/               # route-level screen composition
  hooks/               # reusable behavior and orchestration
  mocks/               # deterministic prototype scenarios
  services/            # external IO adapters
  styles/              # Tailwind entrypoint, CSS variables, global styles
  types/               # genuinely shared contracts
  utils/               # pure helpers
```

Framework-owned conventions take precedence. For example, keep route files where Next.js, Remix, or another router expects them.

## Placement Decisions

| Concern | Default owner | Must not own |
| --- | --- | --- |
| Button, input, badge | `components/ui` | domain data, navigation, fetching |
| Product card, result row | `components/app` or feature components | app-wide orchestration |
| Sidebar shell, detail split | `layouts` | remote data access |
| Route screen | `pages` or framework route | low-level visual primitives |
| Reusable interaction logic | `hooks` or feature controller | presentation markup unrelated to behavior |
| HTTP, persistence, analytics adapter | `services` | rendered UI |
| Scenario fixtures and fake responses | `mocks` | production secrets or live endpoints |

Co-locate files within a feature when that is the repository's established pattern. Layer names describe responsibilities, not mandatory global directories.

## Screen Rule

Keep a screen focused on:

`import -> compose -> connect`

A screen may:

- select a scenario or load route data
- coordinate state shared by its regions
- connect callbacks to navigation or controllers
- compose layouts and domain components

A screen should not contain:

- large repeated JSX blocks
- new primitive implementations
- unrelated parsing or networking logic
- deeply embedded animation timelines
- hardcoded fixture collections mixed with markup

## Extraction Rule

Extract a component when at least one is true:

- structure repeats with controlled variation
- a region has an independent interaction contract
- a visual pattern has meaningful states or variants
- extraction makes the screen easier to read and test
- the design source defines the region as a reusable component

Keep a region local when it is tiny, unique, and clearer in context. Do not create wrappers that only rename a `div`.

## Boundary Rule

Let each layer expose a small public contract. Import through established public entry points when the repository uses them. Avoid deep imports into another feature's private internals.

Prevent cycles by moving shared lower-level concerns downward, not by importing screens into components.

## Prototype Versus Production

Use production-shaped boundaries without production-scale infrastructure:

- deterministic local data instead of a speculative backend
- a simple page owner instead of a global store for local flows
- existing dependencies instead of adding a library for one small behavior
- explicit scenario switching instead of elaborate fixture servers when local mocks suffice

Add complexity only when it makes the prototype answer a real product or interaction question.
