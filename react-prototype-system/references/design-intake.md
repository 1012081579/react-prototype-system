# Design Intake

Use this reference to turn a visual source into implementation evidence before writing JSX.

## Contents

- [Source Priority](#source-priority)
- [Figma Intake](#figma-intake)
- [Screenshot or Image Intake](#screenshot-or-image-intake)
- [Evidence Ledger](#evidence-ledger)
- [Component Inventory](#component-inventory)
- [State Inventory](#state-inventory)
- [Responsive Inference](#responsive-inference)
- [Asset Policy](#asset-policy)
- [Ready-to-Build Gate](#ready-to-build-gate)

## Source Priority

Prefer evidence in this order when sources disagree:

1. The exact frame or component the user named.
2. Explicit annotations, variables, component properties, and prototype links.
3. Repeated patterns in sibling frames and variants.
4. Existing product components and tokens in the repository.
5. Conservative inference.

Call out an inference only when it materially affects behavior, content, or architecture.

## Figma Intake

When a Figma URL or node ID is available:

1. Fetch the named node and its relevant parent context.
2. Capture a screenshot for visual truth.
3. Inspect component instances, variants, variables, text styles, layout constraints, and prototype links.
4. Export or reuse assets through the design source when possible.
5. Inspect sibling frames only when they clarify a state, breakpoint, or transition needed by the task.

Do not traverse the entire file. Stay within the user-scoped feature or flow.

## Screenshot or Image Intake

For a screenshot, identify:

- viewport or aspect ratio
- major regions and their alignment anchors
- fixed, fluid, and content-sized dimensions
- repeated spacing intervals
- typography roles and line wrapping
- surfaces, borders, shadows, and elevation
- image crop behavior and focal points
- controls, selected states, and implied interactions
- clipped or partially visible content that signals scrolling or continuation

Do not assume exact CSS values from appearance alone. Infer relationships first, then tune rendered values through comparison.

## Evidence Ledger

Record high-impact observations in a compact table:

| Evidence | Observation | Implementation consequence | Confidence |
| --- | --- | --- | --- |
| Header alignment | Content aligns to 12-column grid | Reuse page container | High |
| Card image | Fixed 4:3 crop | Use `aspect-ratio: 4 / 3` and `object-fit: cover` | High |
| Mobile frame absent | Desktop cards likely stack | Infer one-column layout and verify | Medium |

Keep low-impact values out of the ledger. The goal is to expose decisions that could otherwise drift.

## Component Inventory

Classify visible regions before coding:

- **Token:** semantic color, type role, spacing role, radius, shadow, motion value.
- **Primitive:** button, input, icon button, badge, separator, avatar.
- **Pattern:** search field, product card, profile summary, filter group, notification row.
- **Layout:** app shell, sidebar layout, detail split, toolbar region.
- **Screen:** route-level composition.
- **Flow:** ordered states and transitions across screens or overlays.

Use visual repetition plus behavioral identity to find component boundaries. Similar rectangles are not automatically one component; identical behavior with a controlled visual variant often is.

## State Inventory

Look for evidence of:

- default, hover, focus, pressed, selected, disabled
- loading, skeleton, populated, empty, error
- validation, success, undo, retry
- open and closed overlays
- first-use and returning-use differences
- role or permission differences
- online and offline behavior

Distinguish states that change layout from states that only change styling. The first group often needs explicit scenarios for visual testing.

## Responsive Inference

Model relationships, not a scaled screenshot:

- Which regions stay fixed?
- Which tracks grow or collapse?
- Which items wrap, scroll, hide, reorder, or change controls?
- Which text is allowed to wrap or truncate?
- Which media keeps an aspect ratio?
- Which actions remain reachable on touch devices?

When only one breakpoint exists, preserve hierarchy and task priority. Do not shrink every dimension proportionally.

## Asset Policy

Build an asset map with source, usage, and crop behavior. Prefer:

1. repository assets already used by the product
2. exports or URLs provided by the design source
3. user-provided files
4. generated or searched assets only when the design leaves the asset open-ended

Never substitute a generic image when the source contains an inspectable product, person, place, or interface state.

## Ready-to-Build Gate

Begin implementation when you can answer:

- What is the first runnable vertical slice?
- Which local components and tokens can be reused?
- What are the component, screen, and flow boundaries?
- Which states must be reachable?
- Which assets are authoritative?
- What changes at a narrow viewport?
- What will be compared in the browser?

If one answer is uncertain, make the smallest reversible assumption and keep it local.
