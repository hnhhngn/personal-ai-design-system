# Design System Spec

Version: **1.2**  
Status: **Active (Additive, AI-first)**

> This document is the **single active Design System Spec** for the personal AI Design System.
> It is a **unified consolidation** of Spec v1.0, v1.1, and v1.2.
>
> All rules here are **additive-only** under v1.x. No breaking change is allowed.

---

## 1. Design Philosophy

### 1.1 AI-first (not human-first)

- This system is designed for **AI to understand, follow, and generate UI consistently over time**.
- Prioritizes **consistency, control, and rule-based extensibility** over free-form creativity.

### 1.2 Token-driven (not implementation-driven)

- All visual decisions (color, spacing, shadow, motion) **must be traceable to tokens**.
- CSS / HTML / JS are implementations, **not the source of truth**.

### 1.3 Visual Language

- Physical / industrial feel
- 3D press & depth perception
- Glass / frosted surfaces for large panels
- Motion is short, intentional, and state-driven

---

## 2. Token Architecture

### 2.1 Token Layers

1. **Foundation Tokens**

   - Color (brand, neutral, surface)
   - Radius
   - Motion (duration, easing)
   - Shadow depth

2. **Component Tokens**
   - Button
   - Knob
   - Sidebar
   - Tag

> Component tokens MUST NOT override foundation tokens without explicit design justification.

---

## 3. Core Components (Locked)

The following components are **core** under Design System v1.x.

> AI MUST NOT modify their default semantics or interaction models.

---

### 3.1 Button

#### Variants

- Button Blue (Primary Action)
- Button Green (Success / Feature Action)
- Button Yellow (Secondary Highlight – v1.1)

#### Shared Behavior

- Physical 3D press effect
- States:
  - Default: elevated
  - Active / Pressed: depressed (reduced shadow + translateY)

#### Rules

- Button Blue remains the primary action
- Button Yellow MUST NOT replace Button Blue
- Button Yellow:
  - Max 1 per view
  - Non-destructive only

---

### 3.2 Knob (Corrected – v1.3)

> **Breaking Correction**
>
> The original Knob interaction model was based on an incorrect assumption.
> This section redefines Knob as a **functional control component** rather than a purely symbolic or decorative element.

---

#### Purpose

- Knob represents a **physical rotary control** similar to volume or brightness knobs.
- It is designed for **incremental value adjustment**, not free-form input.
- Interaction emphasizes **intentional engagement** and **mechanical feedback**.

---

#### Interaction Model

1. **Click**

   - Performs a **depth press** only.
   - No rotation occurs on click.
   - Used for:
     - toggle actions
     - confirm / activate
     - on / off states

2. **Hold + Rotate (Primary Interaction)**

   - Holding the knob **engages control mode**.
   - Rotating while holding **increases or decreases a value**.
   - Rotation has effect **only during hold**.
   - Rotation without holding produces **no effect**.

3. **Removed Behaviors**
   - Click-to-rotate interaction
   - Press-and-hold without rotation

---

#### Physical & Visual Behavior

- Knob MUST visually convey **physical depth**.
- A shadow is required to indicate elevation.
- A pressed state MUST use a **depressed shadow**.
- The shadow layer MUST remain **static**.
- Only the **knob face** rotates.

Conceptual structure:

```
.knob
├─ shadow-layer (static)
└─ face-layer (rotates)
└─ icon
```

---

#### Icon Requirements (Mandatory)

- Knob MUST include an icon.
- Icon provides **directional or functional affordance** (e.g. `+`, `–`, bar, dot).
- Icon MUST:
  - be centered
  - rotate together with the knob face
  - occupy approximately **65% of the knob diameter**
- A knob without an icon is considered **invalid**.

---

#### Usage Constraints

- Knob MUST NOT be used as a text input or free-form form control.
- Decorative or continuous idle animations are not allowed.
- RGB or decorative glow effects are forbidden.

---

### 3.3 Sidebar

#### Surface

- Glass / frosted container

#### Layout

- Desktop:
  - Floating or push-content
  - MUST NOT overlay main content
- Mobile:
  - Overlay with backdrop

---

### 3.4 Tag

#### States

- Inactive
- Active

#### Rules

- Hover only applies when inactive
- MUST NOT replace primary buttons
- No continuous or decorative animation

---

## 4. Motion & Interaction Rules

### 4.1 Motion Principles

- Fast feedback
- Simple easing
- Motion must serve state or feedback

### 4.2 Accessibility

- All motion MUST respect `prefers-reduced-motion`

---

## 5. Extensions (Additive Only)

### 5.1 Button Yellow (v1.1 – Stable)

Semantic intent:

- Secondary highlight
- Attention-required confirmation

Rules:

- Requires Button Blue presence
- Max one instance per view

Token requirements:

- `--button-yellow-bg`
- `--button-yellow-shadow`
- `--button-yellow-shadow-pressed`

---

### 5.2 RGB Effect (v1.2 – Experimental)

#### Purpose

- Decorative ambient accent
- Personal visual signature

#### Allowed Scope

- Decorative containers
- Background frames
- Non-interactive accents

#### Forbidden Scope

- Text
- Icons
- Interactive elements
- Core components (Button, Knob, Sidebar, Tag)

#### Interaction Rules

- Static or slow ambient animation
- MUST NOT react to hover, focus, press

#### Token Requirements

- `--rgb-gradient`
- `--rgb-opacity`
- `--rgb-animation-duration`

---

## 6. Versioning Policy

- v1.x: additive-only
- v2.0: breaking changes (new Spec required)

---

## 7. Relationship to AI-ready Contract

- This Spec defines **meaning and intent**
- AI-ready Contract enforces **machine-level constraints**

> Spec = Understand  
> Contract = Enforce

---

**End of Design System Spec (Unified v1.2)**
