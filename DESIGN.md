# Design System Specification

## 1. Overview & Creative North Star: "The Kinetic Crucible"

This design system is built to transform a standard data dashboard into a high-stakes competitive arena. We are moving away from the static, "admin-panel" aesthetic and toward **"The Kinetic Crucible."** The goal is to evoke the atmosphere of a premiere e-sports broadcast—dark, immersive, and pulsing with energy.

We achieve this through **Intentional Asymmetry** and **Tonal Depth**. Instead of rigid, centered grids, we utilize overlapping layers and offset typography to create movement. Scores aren't just numbers; they are luminous events. The UI should feel like a heads-up display (HUD) projected onto a sleek, obsidian surface.

---

## 2. Colors & Atmospheric Depth

The palette is anchored in deep, midnight tones, allowing neon accents to "pop" with maximum luminance.

### The Palette
*   **Background Canvas:** `background` (#0a0e14) serves as the infinite void.
*   **Team Identities:**
    *   **Blue Team:** `primary` (#69daff)
    *   **Gold Team:** `secondary` (#ffd709)
    *   **Red Team:** `tertiary` (#ff7168)
*   **Surface Foundation:** `surface_container` (#151a21) for base modules.

### The "No-Line" Rule
To maintain a premium, editorial feel, **1px solid borders are strictly prohibited for sectioning.** Boundaries must be defined through background shifts. For example, a `surface_container_highest` module should sit directly on a `surface` background. The contrast in value creates the edge, not a stroke.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of frosted obsidian:
1.  **Level 0 (Base):** `surface` (#0a0e14)
2.  **Level 1 (Sections):** `surface_container_low` (#0f141a)
3.  **Level 2 (Cards/Modules):** `surface_container_high` (#1b2028)
4.  **Level 3 (Floating HUDs):** Semi-transparent `primary_container` or `surface_variant` with a 20px backdrop blur.

### Signature Textures
Main CTAs and "Winner" states must use a **directional gradient** rather than flat fills. Transition from `primary` (#69daff) to `primary_container` (#00cffc) at a 135-degree angle to provide "visual soul."

---

## 3. Typography: Industrial Power vs. Humanist Precision

We utilize a high-contrast typographic pairing to balance technical data with aggressive competition.

*   **The Power Font (Space Grotesk):** Reserved for `display`, `headline`, and `label` roles. Its monolinear, geometric construction mimics technical readouts. Use `display-lg` (3.5rem) for massive score differentials and `label-md` (0.75rem) for technical metadata.
*   **The Functional Font (Manrope):** Used for `body` and `title` roles. It provides the humanist legibility required for player bios, rules, and long-form descriptions.

**Hierarchy Note:** Always uppercase `label` styles in `Space Grotesk` to reinforce the "HUD" aesthetic.

---

## 4. Elevation & Depth: The Glow Principle

In this system, light is the primary communicator of importance.

### The Layering Principle
Achieve depth by stacking surface tiers. A `surface_container_lowest` card placed atop a `surface_container_high` section creates a "recessed" look, while the inverse creates a "raised" look.

### Ambient Shadows & Neon Glows
Standard grey shadows are forbidden. Instead, use **Ambient Glows**:
*   **Shadow Color:** Use a 15% opacity version of the accent color (e.g., `primary` for blue team cards).
*   **Shadow Specs:** `0px 8px 32px` blur. This simulates light reflecting off the dark glass onto the background.

### The "Ghost Border" Fallback
If an edge requires definition for accessibility, use a **Ghost Border**: `outline_variant` (#44484f) at **15% opacity**. It should be felt, not seen.

### Glassmorphism
For floating ranking panels, use:
*   **Background:** `surface_container` at 60% opacity.
*   **Blur:** `backdrop-filter: blur(12px)`.
*   **Edge:** A top-down linear gradient stroke (Ghost Border) to simulate a light catch on the top edge of the glass.

---

## 5. Components

### Interactive Progress Bars
Progress bars are the heartbeat of the dashboard. 
*   **Track:** `surface_container_highest` (#20262f).
*   **Fill:** Linear gradient of the team color (e.g., `secondary` to `secondary_container`).
*   **Effect:** Apply a `box-shadow` glow to the "head" of the progress bar to simulate a burning energy charge.

### Buttons
*   **Primary:** Solid `primary` background with `on_primary` text. No border. Apply a heavy `md` (0.75rem) roundedness.
*   **Secondary/Ghost:** `outline` (#72757d) Ghost Border at 20%. Upon hover, the border becomes 100% opaque accent color with a subtle glow.

### Cards & Leaderboards
**Forbid divider lines.** Use vertical white space (`spacing-6` or 1.5rem) to separate entries. For leaderboards, use alternating surface tones (e.g., Row 1: `surface_container_low`, Row 2: `surface_container_lowest`) to guide the eye without adding visual clutter.

### Team Chips
Use `sm` (0.25rem) roundedness for a sharper, more aggressive look. 
*   **Background:** 10% opacity of team color.
*   **Text:** 100% opacity of team color in `label-md`.

---

## 6. Do's and Don'ts

### Do:
*   **Do** use asymmetrical layouts where the "Primary Score" overlaps the edge of its container.
*   **Do** use `spacing-12` (3rem) and `spacing-16` (4rem) to create large "breathing zones" between major modules.
*   **Do** ensure text on glass surfaces meets AA contrast by using `on_surface` (#f1f3fc).

### Don't:
*   **Don't** use pure white (#ffffff) for anything other than absolute highlights; it breaks the dark-theme immersion. Use `on_background` (#f1f3fc) instead.
*   **Don't** use standard "drop shadows" with black or grey; they look "dirty" on deep blue backgrounds. Always tint your shadows with the accent color.
*   **Don't** use rounded corners larger than `xl` (1.5rem) for main modules; we want "high-energy," not "soft/bubbly."