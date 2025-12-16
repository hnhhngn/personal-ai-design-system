# AI-ready Contract

Version: **1.3**  
Status: **Active (Enforced, Additive-only)**

> This document is the **single active AI-ready Contract** for the personal AI Design System.
> It is a **unified consolidation** of Contract v1.0, v1.1, v1.2, and v1.3.
>
> This contract defines **what AI is allowed or forbidden to do**.  
> It does not explain intent — that belongs to the Design System Spec.

---

## 1. Contract Scope & Authority

```json
{
  "design_system": "Personal AI Design System",
  "contract_version": "1.3",
  "mode": "locked-core",
  "update_policy": "additive-only"
}
```

### Priority Order (highest → lowest)

1. **AI-ready Contract** (this document)
2. **Design System Spec**
3. Generated output (HTML / CSS / JS)

If any conflict exists, **higher priority overrides lower priority**.

---

## 2. Token Enforcement Rules

```json
{
  "token_policy": {
    "require_token_reference": true,
    "allow_hardcoded_values": false,
    "allowed_units": ["px", "%", "ms", "deg", "rgba"],
    "color_invention": false,
    "shadow_invention": false,
    "motion_invention": false
  }
}
```

Rules:

- Every visual value MUST reference a token
- No raw color / shadow / motion values may be invented

---

## 3. CSS Generation Policy

```json
{
  "css_generation": {
    "allowed": true,
    "must_be_token_driven": true,
    "naming_convention": "free",
    "forbidden_patterns": [
      "inline-style",
      "magic-numbers",
      "unscoped-animation"
    ]
  }
}
```

---

## 4. base.css Lock (Read-only Runtime)

```json
{
  "base_css": {
    "role": "token-runtime",
    "source_of_truth": "Design System Spec v1.x",
    "editable": false
  }
}
```

Rules:

- AI MAY read tokens from `base.css`
- AI MUST NOT modify or regenerate `base.css`
- UI code must adapt to tokens, not the reverse

---

## 5. Core Component Lock

```json
{
  "locked_components": {
    "button": {
      "variants": ["blue", "green", "yellow"],
      "behavior": "immutable"
    },
    "knob": {
      "interaction_model": "hold-and-rotate",
      "click_behavior": "depth-press-only",
      "press_hold_behavior": "forbidden",
      "icon_required": true,
      "shadow_required": true,
      "rotation_constraints": {
      "rotation_requires_hold": true,
      "rotate_without_hold": "no-op",
      "shadow_rotates": false,
      "icon_rotates_with_face": true
    },
    "sidebar": {
      "layout_logic": "immutable"
    },
    "tag": {
      "states": ["inactive", "active"],
      "semantics": "immutable"
    }
  }
}
```

AI MUST NOT:

- Change semantics
- Change interaction models
- Replace core components with custom implementations

---

## 6. Variant Control – Button Yellow (Stable)

```json
{
  "button_yellow_rules": {
    "max_instances_per_view": 1,
    "requires_primary_present": true,
    "allowed_roles": ["secondary-highlight", "attention-confirmation"],
    "forbidden_roles": ["primary-action", "destructive-action"]
  }
}
```

Token requirements:

- `--button-yellow-bg`
- `--button-yellow-shadow`
- `--button-yellow-shadow-pressed`

---

## 7. Experimental Feature – RGB Effect

```json
{
  "experimental_features": {
    "rgb_effect": {
      "enabled": true,
      "default": false
    }
  }
}
```

### Allowed Scope

```json
{
  "rgb_effect_scope": {
    "allowed_targets": [
      "decorative-container",
      "background-frame",
      "non-interactive-accent"
    ]
  }
}
```

### Forbidden Usage

```json
{
  "rgb_effect_forbidden": {
    "targets": [
      "text",
      "icon",
      "button",
      "tag",
      "knob",
      "sidebar",
      "form-control"
    ]
  }
}
```

### Token Requirements

- `--rgb-gradient`
- `--rgb-opacity`
- `--rgb-animation-duration`

### Animation Constraints

```json
{
  "rgb_animation_rules": {
    "min_duration_seconds": 8,
    "timing_function": "linear",
    "loop": "infinite",
    "interaction_bound": false
  }
}
```

RGB Effect MAY be used **only if explicitly enabled in CURRENT.md**.

---

## 8. Missing Information Handling

```json
{
  "missing_information_policy": {
    "on_missing_token": "ask",
    "on_missing_variant": "ask",
    "on_missing_behavior": "ask"
  }
}
```

AI MUST:

1. Stop generation
2. Ask a clarification question
3. Wait for confirmation

---

## 9. Versioning Policy

```json
{
  "versioning": {
    "current": "1.3",
    "allow_auto_upgrade": false,
    "breaking_change_allowed": false
  }
}
```

---

## 10. Failure Conditions

Output is **invalid** if AI:

- Violates token rules
- Modifies `base.css`
- Breaks core component locks
- Uses experimental features without opt-in

---

## 11. Contract Summary (For AI)

- This contract is **mandatory**
- Spec defines meaning, Contract enforces behavior
- Consistency > Creativity

---

**End of AI-ready Contract (Unified v1.3)**
