# iKnowAviation UI – Deployment Guide

## Source of Truth
All UI CSS lives in this GitHub repo.

## Production Deployment Paths

### Master UI CSS (global)
Source:
- css/ika_master.css

Deploy to:
- wp-content/plugins/ika-ui-loader-lite/assets/css/ika_master.css

Loaded:
- Site-wide via the IKA UI Loader Lite plugin

---

### Quiz Theme CSS
Source:
- css/ika_quiz.css

Deploy to:
- wp-content/themes/{quiz-child-theme}/ika_quiz.css

Loaded:
- Via WATU PRO theme selection

---

### Flight Deck / Achievements UI
Styles are scoped inside `ika_master.css` under:
- `.ika-scope-flightdeck`

Pages using this UI must include the class:
- ika-scope-flightdeck
