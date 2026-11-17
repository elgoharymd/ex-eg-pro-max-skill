# Design Philosophy

## Principle
Design answers a question: who uses this, for what, and what should they feel or do next? Decoration that does not serve that question is noise.

## Before designing, answer
1. Who is the primary user, and what device and context do they have?
2. What is the one main action on each screen?
3. What must be understood in the first five seconds?
4. What is the brand's character (for example calm, energetic, technical, warm)?
5. What already exists in the product that the design must match?

## Human, not generated

**The highest standard: the design must be unrecognizable as AI output.**

Signs of generic output to avoid:
- Identical card grids with the same radius, shadow, and padding everywhere.
- Hero sections with vague slogans and three equal feature boxes below.
- Purple-to-blue gradients or glass effects applied by default.
- Icons attached to every label whether or not they clarify.
- Lorem-like copy or placeholder metrics left in place.
- Inter, DM Sans, Poppins, Nunito — the AI default font stack (see typography.md).
- SVG icons from a library (Lucide, Heroicons, etc.) — use AI-generated image icons instead (see visual-assets.md).

A human-made design shows choices: a deliberate ratio of white space, one dominant element per view, typography with character, and details that reflect the actual business (real product names, real prices, real photography direction).

**Test:** Ask yourself — could this design be described as "modern and clean"? If yes, it has not been designed yet. Push until it needs a different description.

## Innovation without complexity
Innovation usually means a sharper idea, not more effects. Examples: a layout that reflects the product's workflow, a single distinctive typographic moment, an unusual but readable grid, a color pairing with a clear reason. Simplicity must be designed: fewer elements, each placed exactly.

## Hierarchy
Every view needs an order of importance:
- One primary focal point.
- One or two secondary elements.
- Supporting information that does not compete.
Test it by squinting at the screen or blurring a screenshot. If three things look equally loud, hierarchy has failed.

## Consistency
Components, spacing, color roles, and copy tone must match across pages. A new page that invents its own button style is a defect.

## Decision rule
When two options are both acceptable, choose the one that is clearer, uses existing tokens, and needs less code.
