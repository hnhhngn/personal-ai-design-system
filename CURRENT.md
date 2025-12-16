# Design System – CURRENT

> This file defines the **single active runtime state** of the Personal AI Design System.
>
> AI MUST treat this file as the **only authoritative entry point** for deciding what rules, tokens, and features are active.

---

## Active Files

- **Design System Spec:** `spec.md`
- **AI-ready Contract:** `contract.md`
- **Token Runtime:** `base.css`

---

## Enabled Features

- Button Yellow (secondary highlight variant)
- RGB Effect (Experimental, decorative / ambient only)

---

## Disabled / Not Available

- Any button variants other than Blue, Green, Yellow
- RGB usage outside decorative / ambient scope
- RGB on interactive or core components

---

## Core Guarantees

- Core components are **locked and stable**:

  - Button
  - Knob
  - Sidebar
  - Tag

- Core behavior MUST NOT be modified under Design System v1.x
- All UI MUST be **token-driven**
- `base.css` is **read-only** for AI and applications

---

## AI Usage Instructions (Mandatory)

When generating or modifying UI, AI MUST follow this sequence:

1. Read this file (`CURRENT.md`)
2. Load `spec.md` and `contract.md`
3. Consume tokens exclusively from `base.css`
4. Apply only features explicitly listed as **Enabled**
5. Treat anything not listed here as **not allowed**

If a required capability is missing, AI MUST stop and ask before proceeding.

---

## Versioning & History

- This repository uses **single-file active state**
- Historical versions are tracked via **Git tags**, not file names
- Any change to this file represents an **explicit runtime switch**

---

## Breaking Corrections

### Knob (v1.3)

- Knob interaction model has been **corrected**.
- Click behavior is now **depth press only**.
- Press-and-hold without rotation has been removed.
- Hold + rotate is the primary interaction for value adjustment.
- Knob now **requires**:
  - physical shadow with pressed state
  - static shadow (does not rotate)
  - mandatory icon (~65% of knob size)

Any previous click-to-rotate behavior is **invalid** and must not be used.

---

**End of CURRENT.md**
