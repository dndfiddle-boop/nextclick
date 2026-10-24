# esu.edu homepage fixture (captured October 24, 2026 via Firecrawl)

Source: https://www.esu.edu/ (status 200). Captured because this container cannot reach esu.edu directly.

## Where "Faculty & Staff" actually lives (verified from the captured link list)
- NOT in the five visible top-nav sections (Academics, Admissions & Aid, Life at ESU, Warrior Outcomes, About ESU).
- Inside the hamburger "Menu" overlay, under the heading "Tools and Support For:" -> Faculty & Staff -> https://www.esu.edu/faculty-staff/index.php
- Same overlay, tools list -> "Faculty & Staff Directory" -> https://www.esu.edu/faculty-staff/directory.php
- About ESU submenu -> "Faculty & Staff Directory" (same directory URL)
- Footer -> Faculty & Staff (same index URL)

## Duplicate-label hazard for the model
Two different targets share the words "Faculty & Staff":
- "Faculty & Staff" (landing page, /faculty-staff/index.php)
- "Faculty & Staff Directory" (people search, /faculty-staff/directory.php)
Task A expects the landing page. If the user says "find my profile", the directory is right instead. Clarification state should trigger when the goal is ambiguous between these.

## Implication for Task A page states
1. Homepage, menu closed: correct target = the "Menu" button (top right). Reason to show: "Faculty & Staff is inside the menu."
2. Menu open: correct target = "Faculty & Staff" under "Tools and Support For".
3. Scrolled to footer: "Faculty & Staff" footer link is an acceptable alternative target.
Links into login systems (D2L, WFish, Email) also appear in the menu and must never be chosen for Task A.
