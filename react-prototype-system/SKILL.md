---
name: react-prototype-system
description: Turn Figma frames, screenshots, visual specifications, or existing UI designs into high-fidelity, runnable React prototypes through a component-driven design-engineering workflow, defaulting new or unconstrained implementations to TypeScript and Tailwind CSS. Use when Codex is asked to reconstruct React components, screens, flows, design-system explorations, product concepts, or front-end mock applications from a design source; evolve a React prototype without collapsing its architecture; or review a design-to-code implementation for fidelity, component boundaries, interaction states, responsiveness, accessibility, and composition.
---

# React Prototype System

Build the experience as a system, then compose the screens. Optimize first for learning, interaction, fidelity, and changeability while leaving a clear path to production.

## Core Contract

Apply these rules throughout the task:

1. Inspect the design source and repository before writing code.
2. Preserve the repository's framework, conventions, tokens, components, and tooling unless the task requires a greenfield setup.
3. Default new or otherwise unconstrained React implementations to TypeScript and Tailwind CSS. In an existing repository, use them when present; do not migrate a coherent local stack unless the user requests it.
4. Work from experience and flow to components and implementation:

   `experience -> interaction flow -> states -> component contracts -> tokens -> implementation`

5. Build dependencies from lower layers to higher layers:

   `tokens -> primitives -> patterns -> layouts -> screens -> flows`

6. Prefer stateless display components controlled by explicit props and callbacks.
7. Keep mock data, side effects, navigation, and orchestration outside reusable display components.
8. Implement the primary path and at least one relevant failure or recovery path.
9. Use real design assets when provided. Do not replace inspectable product imagery or icons with vague placeholders.
10. Verify behavior and visual fidelity in a running browser at representative desktop and mobile sizes.
11. Stop adding architecture when it no longer improves learning, fidelity, reuse, or changeability.

Treat these as defaults, not permission to fight an established codebase. Local patterns win when they already solve the same problem coherently.

## Workflow

### 1. Classify the Request

Identify all three dimensions before implementation:

- **Code context:** existing application, isolated package, or greenfield prototype.
- **Design scope:** component, screen, multi-screen flow, or design-system exploration.
- **fidelity target:** exact reconstruction, close interpretation, or open-ended concept.

If the user does not specify fidelity, reproduce the supplied design closely. Do not redesign it merely to make implementation easier.

If implementation tooling is unspecified, use TypeScript and Tailwind CSS for a greenfield or otherwise unconstrained prototype. Do not migrate an established project solely to enforce this default.

### 2. Gather Evidence

Inspect the repository for framework, routes, TypeScript configuration, Tailwind or other styling setup, tokens, icon libraries, assets, state libraries, test commands, and component conventions. Inspect every relevant design frame, variant, breakpoint, annotation, and asset.

Record the minimum working model needed to implement confidently:

- visual hierarchy and geometry
- typography, color, spacing, radii, borders, and shadows
- reusable regions and variants
- interactive controls and transitions
- loading, empty, error, permission, and recovery states that are shown or implied
- desktop/mobile relationships
- required images, icons, fonts, and content

Read [design-intake.md](references/design-intake.md) for Figma, screenshot, visual-spec, or incomplete-design tasks. For a substantial flow, copy [prototype-brief.md](assets/prototype-brief.md) into a temporary working note and fill only the useful sections.

### 3. Model Before JSX

Create four small internal artifacts before coding:

1. A screen or flow map.
2. A component inventory grouped by layer.
3. A state and scenario matrix.
4. An asset and responsive-behavior map.

Do not turn these into user-facing documentation unless requested. Use them to resolve ownership and prevent page-first sprawl.

Read [architecture.md](references/architecture.md) when deciding layers, folder placement, dependency direction, or greenfield structure.

### 4. Establish the Visual Foundation

Map design evidence to the existing design system first. Add or extend tokens only for values that recur or carry semantic meaning. Keep one-off composition values local when turning them into global tokens would create noise.

Establish, in this order:

1. font loading and text roles
2. color and surface roles
3. spacing and layout constraints
4. radius, border, shadow, and elevation roles
5. motion durations and easing when motion is part of the design

Do not use a generic theme as a substitute for reading the source.

When using Tailwind CSS, map recurring design semantics into the existing Tailwind theme or CSS variables. Prefer configured utilities over repeated arbitrary values, while keeping true one-off composition values local.

### 5. Build Bottom-Up

Implement the smallest coherent vertical slice while maintaining layer direction:

1. Reuse or extend existing primitives.
2. Build reusable visual patterns.
3. Add domain components that accept data and callbacks.
4. Compose layouts and screens.
5. Connect routes, state transitions, and mock behaviors.

Do not prebuild a complete abstract design system before the first working screen. Extract reusable pieces as evidence appears, and keep screen-specific composition close to the screen.

Write React components in `.tsx` and non-JSX modules in `.ts` when the default stack applies. Use Tailwind utility classes for component styling and responsive behavior, following any class-merging and variant conventions already present.

Read [component-contracts.md](references/component-contracts.md) when defining component boundaries, props, variants, TypeScript types, or semantic behavior. The optional [create_component.py](scripts/create_component.py) helper may scaffold a stateless host-element component in a greenfield project; do not use it when the repository has a different generator or file convention.

### 6. Make States and Data Deliberate

Place state at the narrowest owner that coordinates every consumer. Keep derived values derived. Keep server or mock data separate from display components. Represent mutually exclusive statuses explicitly instead of combining contradictory booleans.

Create deterministic mock scenarios for the states needed to evaluate the design. At minimum include:

- the primary populated state
- one relevant failure, empty, permission, or recovery state

Add loading, long text, overflow, first-use, offline, and destructive-action states when the product surface makes them plausible or the source shows them.

Read [state-and-mocks.md](references/state-and-mocks.md). Copy [state-matrix.md](assets/state-matrix.md) only when a multi-state prototype needs a persistent scenario inventory.

### 7. Complete the Interaction Flow

Make controls perform their implied actions. Connect navigation, menus, tabs, dialogs, filters, forms, undo, retry, and dismissal as the design requires. Prefer a deterministic local simulation over dead controls or unnecessary backend work.

Keep screens focused on `import -> compose -> connect`. Move reusable behavior into hooks or controllers and side effects into services or existing data layers.

Read [flows-motion-responsive.md](references/flows-motion-responsive.md) for page composition, flow modeling, motion boundaries, responsive behavior, and accessibility.

### 8. Verify in the Browser

Run the application and validate the actual rendered result. Use browser screenshots and DOM or console inspection where available.

Verify in this order:

1. route loads and the main flow completes
2. major regions, geometry, and responsive constraints match
3. typography, assets, color, and surfaces match
4. states, focus, keyboard behavior, and recovery work
5. motion supports the transition and respects reduced motion
6. tests, type checks, lint, and build pass as supported by the repository

Compare against the source at representative design dimensions and at least one narrow viewport. Fix the largest perceptual or behavioral mismatch first, then repeat.

Read [verification.md](references/verification.md) before declaring the task complete.

## Reference Routing

Load only the references needed for the current task:

| Need | Read |
| --- | --- |
| Interpret a Figma frame, screenshot, annotation, or asset set | [design-intake.md](references/design-intake.md) |
| Choose layers, folders, imports, or greenfield structure | [architecture.md](references/architecture.md) |
| Define component APIs, props, variants, semantics, or types | [component-contracts.md](references/component-contracts.md) |
| Decide state ownership, data boundaries, or mock scenarios | [state-and-mocks.md](references/state-and-mocks.md) |
| Compose pages, interactions, motion, responsive behavior, or accessibility | [flows-motion-responsive.md](references/flows-motion-responsive.md) |
| Review fidelity, behavior, code quality, and completion | [verification.md](references/verification.md) |

## Completion Gate

Do not call the prototype complete until all applicable statements are true:

- The intended route or entry point renders without runtime errors.
- New or otherwise unconstrained React code uses TypeScript and Tailwind CSS.
- The primary flow is usable from start to finish.
- A relevant alternate, failure, or recovery state is reachable.
- Reusable display components do not fetch, navigate, or own unrelated business state.
- Supplied assets are used correctly and no inspectable content is replaced by arbitrary placeholders.
- Desktop and narrow layouts are coherent and free of unintended overlap or clipping.
- Interactive elements use appropriate semantics, labels, focus behavior, and keyboard access.
- The result has been visually compared with the design source after rendering.
- Supported checks pass, or remaining failures are reported with their cause.

## Anti-Patterns

Correct these immediately when encountered:

- starting with a monolithic page and extracting only after it becomes unmanageable
- duplicating an existing local primitive or icon
- placing fetches, routing, or global state inside a visual card or row
- inventing a prop for every possible future need
- using boolean combinations that permit impossible states
- hardcoding business data in JSX instead of passing data or using mocks
- treating one desktop frame as proof of responsive behavior
- adding motion inside every component instead of at transition boundaries
- declaring visual fidelity from code inspection without running the interface
- replacing a supplied product asset with a generic stock image, emoji, or hand-drawn substitute
- introducing JavaScript or a parallel styling system when TypeScript and Tailwind CSS are the selected defaults
