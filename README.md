# iKnowAviation – Site UI (CSS + Templates)

This repo stores the UI layer for iKnowAviation (IKA): shared CSS utilities, quiz + results styling, and Flight Deck/profile styling used on the WordPress + Elementor site.

## What’s in this repo

### `css/ika_master.css` (Global / Shared UI)
**Purpose:** Site-wide design system + shared components used across multiple pages and templates.

**Key behaviors:**
- **Design tokens:** CSS variables (colors) live in `:root` (navy, blue, amber, surfaces, borders, text).
- **Elementor defaults:**
  - Sets a global `.elementor-button` style (pill radius, Montserrat, uppercase tracking, hover lift + shadow).
  - Provides wrapper “button variants”:
    - `.ika-btn-primary .elementor-button` (solid blue)
    - `.ika-btn-secondary .elementor-button` (dark w/ border)
    - `.ika-btn-ghost .elementor-button` (outline/ghost)
    - `.ika-btn-link .elementor-button` (link-style)
- **Shared components:**
  - `.ika-card` (white card with border + hover lift).
  - `.ika-dark` (dark section skin: heading, text, link colors).
- **Forms:**
  - Generic form system: `.ika-form` styles labels + inputs + focus ring + error states.
  - **UsersWP forms:** consistent label visibility + input styling + unified UsersWP submit buttons.
- **XP UI components:**
  - `.ika-leaderboard` table-like layout for XP leaderboard.
  - `.ika-xp-progress-*` progress bar wrapper, fill, and meta text.
- **Modal theming (jQuery UI):**
  - Shared styling for achievement modals:
    - WATU Play modal: `#watuproplay-modal` (via `.ui-dialog[aria-describedby="watuproplay-modal"]`)
    - Rank-up modal: `.ika-rankup-dialog` / `#ika-rankup-modal`
  - Includes a consistent titlebar and a custom close button “×”.
- **Daily Missions (shared block):**
  - `.ika-dm-*` styles mission wrapper, cards, status badges, meta row, and stats grid.
- **Avatar level ring + badge:**
  - `.ika-level-avatar-wrapper` applies ring/glow around avatar.
  - `.ika-level-badge` positions “Lv X” badge on the avatar.

---

### `css/ika_quiz.css` (WATU PRO Quiz + Results Theme)
**Purpose:** Dark “quiz shell” styling for WATU PRO quiz pages and final results pages.

**Key behaviors:**
- **Quiz and Results shell:** `.ika-quiz-page` + `.ika-results-page` create a centered card with rounded corners, dark background, and shadow.
- **Shared hero header:** `.ika-hero` with overlay (`::before`) for legibility, supports hero variants (e.g., `.hero-jet`).
- **Quiz answer choices:**
  - Styles `.watupro-question-choice label` into pill buttons.
  - Hides radio/checkbox inputs inside WATU answer choices.
  - Selected answers on quiz page become a blue pill.
- **Results answer evaluation styling:**
  - Uses question-level classes from WATU:
    - `.watupro-resolved` = answered correctly
    - `.watupro-unresolved` = answered incorrectly
  - Uses `li[class*="user-answer"]` for the **selected** answer.
  - Correct selected answer => **green pill + ✓**
  - Incorrect selected answer => **red pill + ✕**
  - Non-selected choices remain neutral dark pills.
- **Results layout styling:**
  - Stats grid (`.ika-stats-grid`), CTA buttons (`.ika-btn-*`), answer sections, typography normalization.
- **Hides comment box:**
  - Hides `.watupro-user-feedback` and wrapper paragraph that contains it.
- **WATU Play modal styling (in this file as well):**
  - Adds “gold ring” treatment + titlebar spacing + modal content layout for badge/level presentation.

---

### `css/ika_flight_deck.css` (Flight Deck / Profile Hub)
**Purpose:** Dark Flight Deck “profile hub” shell that visually matches quiz/results styling.

**Key behaviors:**
- **Main shell:** `.ika-profile-hub` creates a rounded dark card layout similar to quiz/results.
- **Hero layout:** `.ika-hub-hero` header with overlay; flex layout for:
  - Left side: avatar + name + status (`.ika-hub-hero-left`)
  - Right side: CTAs (`.ika-hub-hero-right`)
- **Metrics strip:** `.ika-hub-metrics-inner` grid with responsive breakpoints.
- **Section wrappers:** `.ika-hub-section-*` shared titles/kickers/links.
- **Rank + XP:** `.ika-hub-rank-xp` grid with rank ladder track and XP progress visuals.
- **Missions:** `.ika-hub-missions-grid` layout plus guard rules that prevent “legacy absolute positioning” issues.
- **Badges & achievements:** grid layout, badge icons, upcoming upgrades list.
- **Leaderboard + flight log:** table styling, filters, “me” highlight row, summary + table cards.
- **Account & preferences:** card layout + UsersWP-safe positioning reset + checkbox list styling.
- **Responsive rules:** breakpoints for hero stacking, grid column changes, and card layouts.

---

## How these files are intended to work together

Typical load order:
1. `css/ika_master.css` (global design system + shared components)
2. `css/ika_quiz.css` (quiz + results theme + WATU-specific styling)
3. `css/ika_flight_deck.css` (Flight Deck/profile hub overrides and layouts)

In general:
- `ika_master.css` defines reusable UI primitives.
- `ika_quiz.css` defines WATU quiz/results presentation and special behaviors.
- `ika_flight_deck.css` defines the Flight Deck layout that consumes shared components.

---

## Editing guidelines (recommended)

- Keep **global/shared utilities** in `ika_master.css`.
- Keep **WATU quiz/results behaviors** in `ika_quiz.css`.
- Keep **Flight Deck layout** in `ika_flight_deck.css`.
- When adding new rules:
  - Prefer **scoped selectors** (e.g., `.ika-profile-hub ...`) to avoid site-wide collisions.
  - Avoid `!important` unless you are overriding plugin inline styles or Elementor output.
- If you do a “clean pass”:
  - Reorder/organize only (no intentional visual changes).
  - Deduplicate exact repeats where later rules already override earlier ones.

---

## Notes
- WATU PRO and WATU Play generate specific markup/classes that these styles depend on.
- jQuery UI Dialog styling is used for WATU Play achievement modals and rank-up modals.
