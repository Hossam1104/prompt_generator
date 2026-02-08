# Mission Plan — Prompt Generator UI

## Objective

Produce **one single HTML file only** named **`prompt_generator.html`** that contains **HTML + CSS + JavaScript (or TypeScript transpiled to JS)** embedded inline. No external dependencies, no build steps, no frameworks.

The HTML file must generate **enterprise-grade QA prompts** dynamically, based on structured user inputs, and output a **single consolidated prompt text** ready to be copied and used as-is.

---

## Global Constraints (Non‑Negotiable)

* Output **ONLY** one file: `prompt_generator.html`
* All logic and styling must be inline
* No placeholders
* No lorem ipsum
* No example-only logic
* No backend calls
* Deterministic behavior
* Audit‑ready UI and output

Failure to meet any constraint invalidates the solution.

---

## UI Structure

### Tabs

Implement a tab-based UI. Tabs must be extensible for future prompt types.

#### Tab 1 — **Test Scenarios Generation** (Mandatory)

This tab is required in this mission.

---

## Input Fields (Test Scenarios Generation Tab)

The UI **must include the following inputs**:

1. **Target Platform**
   Select input with options:

   * Desktop
   * Web
   * Mobile
   * APIs

2. **Technology Used**
   Free-text input supporting combined stacks, e.g.

   * Angular + .NET
   * Flutter + Laravel

3. **Total Test Case Count (Global)**
   Numeric input.

   **Rules:**

   * This value represents the **minimum required test cases per section**.
   * Any generated section producing fewer test cases than this number is considered a **failure by definition**.
   * The number must be injected explicitly into the generated prompt text.

4. **Story Title**
   Single-line text input.

5. **Story Description**
   Multi-line textarea.

6. **Additional Business Rules / Notes**
   Multi-line textarea.

---

## Prompt Generation Logic

### Core Requirement

When the user clicks **Generate Prompt**, the system must:

* Construct **one large text output**
* Preserve the **entire enterprise QA master prompt** provided below
* Dynamically replace contextual sections using the **6 user inputs**
* Inject the values explicitly into the prompt (not summarized, not referenced)

The output must be shown inside a **read-only textarea** below the inputs.

---

## Buttons

* **Generate Prompt**
  Builds the prompt text and renders it in the output textarea.

* **Copy Prompt**
  Copies the full generated prompt to clipboard.

Visual feedback (success state) is recommended but not mandatory.

---

## Dynamic Injection Rules

The following parts of the master prompt must be **dynamically replaced** every time:

* Target Platform → from input (1)
* Technology Stack → from input (2)
* Test Case Count → from input (3)
* Story Title → from input (4)
* Story Description → from input (5)
* Business Rules / Notes → from input (6)

No other content may be altered.

---

## Master Prompt Template (Immutable Except Dynamic Fields)

The generator must output **exactly** the following prompt text, with dynamic values merged in.

---

🔐 ROLE & EXECUTION CONTEXT (ENTERPRISE / NON-NEGOTIABLE)

Act as a Principal / Senior Software Quality Assurance Engineer operating within a large-scale, production-grade enterprise environment governed by:

• Strict QA governance
• Auditability
• Regulatory compliance
• Formal release sign-off

You are executing a QA deliverable, not assisting, explaining, summarizing, or teaching.

Your output MUST be suitable for:

• Enterprise audit
• Regulated release sign-off
• Immediate manual execution
• Automation readiness (Cypress / Playwright / Selenium compatible)

⚠️ Any deviation from instructions is a HARD FAILURE.

---

🌐 APPLICATION CONTEXT (IMMUTABLE)

Target Platform: **<USER_TARGET_PLATFORM>**
Technology Stack: **<USER_TECH_STACK>**

Connectivity: Online only (❌ No offline or cached behavior)

---

🧠 ASSUMPTIONS (MANDATORY)

• Production-grade data sensitivity
• Backend is the single source of truth
• Stateless frontend
• Role-based access control enforced server-side

Zero tolerance for:

❌ Data corruption
❌ Partial writes
❌ UI-only validation
❌ Undefined or inconsistent states
❌ Silent API failures

---

📌 INPUT FORMAT (STRICT)

You will receive ONE dashboard user story only, enclosed exactly as follows:

//Start Story//
Title: <USER_STORY_TITLE>

Description:
<USER_STORY_DESCRIPTION>

Additional Business Rules / Notes:
<USER_BUSINESS_RULES>
//End Story//

❌ You MUST NOT assume missing requirements are out of scope.

---

🎯 OBJECTIVE — COVERAGE EXPANSION MODE

Generate a MAXIMALLY EXHAUSTIVE, EXECUTION-READY TEST SUITE.

Your goal is risk elimination, not documentation.

---

🔢 GLOBAL TEST CASE COUNT RULE (ABSOLUTE)

Each test section MUST contain **AT LEAST <USER_TEST_COUNT> FULLY DEFINED TEST CASES**.

If ANY section produces fewer than this number → THE OUTPUT IS INVALID.

---

🧱 TEST CASE ATOMICITY (MANDATORY)

EVERY test case MUST be fully standalone and atomic.

Each test case MUST include:

• Unique Test Case ID
• Clear, business-readable title
• Scenario Type
• Priority (P0–P3)
• Case-specific Preconditions
• ≥ 6 numbered test steps
• ≥ 5 explicit expected results

---

📐 MINIMUM DEPTH RULE (NON-NEGOTIABLE)

Each test case MUST explicitly verify:

✔ UI behavior
✔ API request payload & headers
✔ Backend response code
✔ Database impact
✔ Navigation or UI state outcome

---

🔁 CONTROLLED DELIVERY MODE (MANDATORY)

Deliver ONE section at a time.

Do NOT proceed unless explicitly instructed:

CONTINUE – <SECTION NAME>

---

🧨 FINAL COMPLIANCE GATE

If ANY rule is violated → REGENERATE FROM SCRATCH.

The output MUST be audit-ready, enterprise-compliant, and execution-grade.

---

## Technical Implementation Notes

* Use semantic HTML
* Minimal but professional styling
* JS must be readable and deterministic
* No frameworks
* No eval
* No external assets

---

## Deliverable

The final answer generated by the AI **must only be the content of `prompt_generator.html`**.

Nothing else.

---

## Modifications History (Post-Initial Implementation)

### ✅ Corrective Refactor — Enterprise Edition (v2.0)

The following modifications were applied to the original implementation to enhance functionality, fix defects, and align with updated enterprise requirements:

#### 1. **Typography Enhancement**

**Change:** Replaced system font stack with **Cairo** font family

**Implementation:**
* Added Google Fonts CDN link for Cairo (weights: 400, 600, 700, 800)
* Applied `font-family: 'Cairo', sans-serif` globally to body, inputs, buttons, and output textarea
* Ensures consistent, modern, professional appearance across all UI elements
* Provides excellent multilingual support (Arabic + Latin)

#### 2. **Field Validation Removal (Critical Bug Fix)**

**Change:** Removed ALL field validations — made all inputs optional

**Rationale:**
* Original implementation incorrectly enforced mandatory inputs
* New requirement: Nothing is mandatory
* QA engineers must have flexibility to generate prompts with partial information

**Implementation:**
* Removed `if (!field) { alert(...); return; }` validation logic
* Removed `required` CSS class and asterisk markers
* Removed `disabled selected` from platform dropdown default option
* Empty fields now inject as empty strings (intentional behavior)
* Generate button always executes regardless of input state

#### 3. **UI/UX Modernization**

**Change:** Enhanced visual design to be modern, catchy, and enterprise-grade

**Implementation:**

* **Color Scheme:**
  * Primary: Indigo (#4f46e5) with gradient variations
  * Accent: Cyan (#06b6d4)
  * Replaced flat colors with gradient backgrounds

* **Visual Enhancements:**
  * Header: Linear gradient with decorative radial overlays
  * Buttons: Gradient backgrounds with hover/active states
  * Cards: Soft shadows (3-tier system: sm, md, lg)
  * Borders: Rounded containers (8px/12px radius)
  * Focus states: Ring glow effect (4px rgba blur)

* **Animations:**
  * Fade-slide up transition for output sections (400ms ease-out)
  * Button scale transform on active state (0.985)
  * Smooth hover transitions (0.2-0.25s)

* **Layout:**
  * 2-column form grid (mobile: 1-column responsive breakpoint at 640px)
  * Improved spacing and visual hierarchy

#### 4. **Section Titles Feature (New)**

**Change:** Added automatic test category title generator

**Implementation:**

* **New UI Section:** "Section Titles" displayed above the generated prompt
* **7 Category Titles:** Auto-generated in format `TS_<Story Title> (<CATEGORY>)`
* **Categories:**
  1. ✅ HAPPY PATH
  2. ❌ NEGATIVE & VALIDATION
  3. ⚠️ EDGE & BOUNDARY
  4. 🎨 UI / UX
  5. 🔄 NAVIGATION & STATE
  6. 🔐 SECURITY & DATA INTEGRITY
  7. 🚦 PERFORMANCE & STABILITY

* **Features:**
  * Each title displayed in a clickable chip
  * Individual copy button per title
  * Inline "Copied!" feedback (1.5s fade)
  * "US" prefix automatically stripped from story title
  * Emoji indicators for visual categorization

* **CSS:**
  * `.titles-section` — Container with fade-slide animation
  * `.title-chip` — Individual title with hover states
  * `.chip-copied` — Fade-in/out feedback label

* **JavaScript:**
  * `cleanStoryTitle()` — Regex-based US prefix removal
  * `copyChip()` — Individual title clipboard copy
  * `showChipCopied()` — Feedback animation control

#### 5. **Enhanced Prompt Template**

**Change:** Replaced generic prompt with comprehensive Gazer-specific template

**New Sections Added:**

* **Enhanced Role Context:**
  * Changed from "Senior Software QA" to "Senior **Web** Software QA Engineer"
  
* **Expanded Application Context:**
  * Added: Application Type (Web Dashboard)
  * Added: Frontend Framework (Angular - Enterprise SPA)
  * Added: Backend (PHP - RESTful APIs)
  * Added: Database (MySQL)
  * Added: Authentication (Token-based JWT/Session)
  * Added: Business Domain (Gazer - enterprise, transaction-driven, multi-user)
  * Kept: Target Platform (dynamic from user input)
  * Kept: Technology Stack (dynamic from user input)

* **Scope Non-Reduction Rule (New):**
  * Prohibits reducing coverage based on simplicity assumptions
  * Addresses "just UI" or "admin-only" justifications
  * Enforces full enterprise-grade coverage regardless of story type

* **Mandatory Minimum Test Case Counts Table (New):**
  * Replaces single global count with per-category minimums:
    * Happy Path: 10–15
    * Negative / Validation: 15–25
    * Edge & Boundary: 10–20
    * UI / UX: 12–20
    * Navigation & State: 8–15
    * Security & Data Integrity: 8–12
    * Performance & Stability: 6–10
  * User's global count still injected as absolute minimum

* **Absolute Anti-Outline Rule (New):**
  * Strictly forbids outlines, grouped scenarios, shared steps
  * Prohibits placeholder text, ID ranges, "same as above"
  * Bans generic phrases like "handled gracefully", "no crash"
  * Includes regeneration requirement if detected

* **Enhanced Test Case Atomicity:**
  * Added explicit scenario type requirement (Happy/Negative/Edge/UI/Navigation/Security/Performance)
  * Increased from "≥ 6 steps" to "Atomic, numbered test steps (≥ 6 steps)"
  * Increased from "≥ 5 expected results" to "Explicit, verifiable expected results (≥ 5 assertions)"

* **Enhanced Minimum Depth Rule:**
  * Changed "UI behavior" to "**Angular** UI behavior"
  * Changed "Database impact" to "Database impact (write / no-write / rollback / **aggregation accuracy**)"
  * Changed "Navigation or UI state" to "Navigation, **routing**, or UI state outcome"

* **Required Test Suite Structure (New):**
  * **Section 1 — General Preconditions:** Must-have items listed (Angular deployed, production build, auth state, browser compatibility, MySQL data, etc.)
  * **Section 2 — Test Scenarios & Test Cases:** All 7 categories explicitly listed

* **Controlled Delivery Mode (Enhanced):**
  * Added requirement to state: delivered count, required minimum, compliance status
  * Clarified section-by-section progression with explicit "CONTINUE – <SECTION NAME>" instruction

* **Self-Audit & Failsafe (New):**
  * Added pre-finalization verification checklist
  * Requires internal verification before responding
  * Auto-regeneration rule if violations detected

* **Final Compliance Gate — Kill Switch (New):**
  * Explicit failure condition: missing count, outline content, forbidden patterns
  * Requires full regeneration from scratch

* **Final Output Requirements (New):**
  * Executable without clarification
  * Suitable for manual + automation
  * Audit-ready and enterprise-compliant
  * Reflects real Gazer dashboard business risk
  * Zero placeholders or summaries

#### 6. **Story Input Format Enhancement**

**Change:** Modified how story content is injected into prompt

**Before:**
```
//Start Story//
Title: <USER_STORY_TITLE>

Description:
<USER_STORY_DESCRIPTION>

Additional Business Rules / Notes:
<USER_BUSINESS_RULES>
//End Story//
```

**After:**
* Story block uses raw title (preserves "US" prefix in story context)
* Description and Business Rules only injected if non-empty
* Format: `Title\n\nDescription:\n<desc>\n\nAdditional Business Rules / Notes:\n<rules>`
* Added clarification text: "The story may include: Business rules, UI behaviors, Validation rules, API constraints, Role restrictions, Acceptance criteria, Edge cases, Implicit enterprise risks"

#### 7. **Copy Feedback Enhancement**

**Change:** Replaced blocking `alert()` with inline, non-blocking feedback

**Implementation:**
* Added `.copy-feedback` element with fade animation
* Shows "Copied to clipboard" message for 2.2 seconds
* Uses CSS transitions instead of JavaScript timing
* Maintains clipboard fallback for older browsers (execCommand + clipboard API)

#### 8. **Form Layout Optimization**

**Change:** Adjusted form grid to accommodate all 6 inputs efficiently

**Implementation:**
* Platform, Technology, Test Count: Single-width columns (row 1)
* Story Title: Single-width column (row 2)
* Story Description: Full-width (row 3)
* Business Rules: Full-width (row 4)
* Note added under Story Title: "The 'US' prefix will be automatically removed for section titles."

#### 9. **Documentation**

**Added:** `README.md` — Comprehensive project documentation

**Includes:**
* Project overview and features
* Usage guide with workflow example
* Technical specifications and design system
* File structure and design decisions
* UI/UX guidelines and interaction patterns
* Requirements compliance matrix
* Version history (v1.0 → v2.0)
* Browser compatibility and testing notes
* Contact information and license

#### 10. **Advanced Technology Stack Dropdown System (Phase 6)**

**Change:** Converted "Technology Used" from free-text input to intelligent platform-dependent dropdown with visual tech component badges

**Implementation:**

* **Tech Stack Mapping Object:**
  * 4 platforms with dynamic technology combinations
  * 8 total tech stack configurations:
    * Desktop: WPF + .NET + MSSQL (1 option)
    * Web: Angular-Laravel-MySQL, Angular-.NET-MSSQL (2 options)
    * Mobile: Flutter-Laravel-MySQL, Flutter-.NET-MSSQL (2 options)
    * APIs: Laravel-MySQL, .NET-MSSQL (2 options)

* **Default Values:**
  * Platform: Web (pre-selected on page load)
  * Technology: Angular-Laravel-MySQL (first Web option, auto-selected)

* **Dynamic Dropdown Population:**
  * `updateTechStack()` — Populates tech dropdown based on selected platform
  * Triggered on platform change via `onchange="updateTechStack()"`
  * Tech dropdown cleared and repopulated with platform-specific options
  * Previous selection lost on platform change (intentional)

* **Visual Tech Badges:**
  * `updateTechBadges()` — Renders visual component breakdown
  * Triggered on technology selection via `onchange="updateTechBadges()"`
  * Creates individual gradient badges for:
    * **Frontend Component** (e.g., Angular) — Monitor icon, cyan gradient
    * **Mobile Component** (if applicable, e.g., Flutter) — Mobile icon, cyan gradient
    * **Backend Component** (e.g., Laravel, .NET) — Server icon, cyan gradient
    * **Database Component** (e.g., MySQL, MSSQL) — Database icon, cyan gradient
  * Each badge displays technology name with inline SVG icon
  * Badges appear below tech dropdown, auto-hide on new selection

* **UI/UX Features:**
  * Platform emoji indicators: 🖥️ (Desktop), 🌐 (Web), 📱 (Mobile), ⚙️ (APIs)
  * Tech badges use cyan gradient (#06b6d4 → #0891b2)
  * Tech badges have subtle shadow (0 2px 8px rgba(6, 182, 212, 0.2))
  * Smooth 400ms fade-slide animation on tech badge refresh
  * Inline `.tech-stack-badges` container with flex wrap layout

* **CSS Additions:**
  * `.tech-stack-badges` — Flex container (gap: 8px, flex-wrap)
  * `.tech-badge` — Gradient background, cyan color, 20px border-radius, 5px padding, inline-flex with SVG support

* **JavaScript Logic:**
  * `techStackMap` object structure:
    ```javascript
    {
      'Platform': [
        { value: 'id', label: 'Full Label', frontend/mobile: 'Tech', backend: 'Tech', database: 'Tech' }
      ]
    }
    ```
  * SVG icons for each component type (4 custom icons):
    * Monitor (16×24 viewBox) — Frontend badge icon
    * Mobile (14×20 viewBox) — Mobile badge icon
    * Server/Rack (18×11 viewBox) — Backend badge icon
    * Database/Cylinder (18×17 viewBox) — Database badge icon

* **Backward Compatibility:**
  * Tech stack value (e.g., "angular-laravel-mysql") injected into prompt template
  * Full formatted label (e.g., "Frontend Angular + Backend Laravel + Database MySQL") injected as `<TECH_STACK>` variable
  * Prompt generation still works with dropdown values instead of text input
  * All 6 input fields remain functional and required

* **Prompt Integration:**
  * Technology Stack field in generated prompt now shows formatted label with component breakdown
  * Example: "Technology Stack: **Frontend Angular + Backend Laravel + Database MySQL**"
  * Supports audit-ready documentation of selected tech stack

#### 11. **Bugs Enhancement Prompt Tab (Phase 7)**

**Change:** Added a new tab and prompt generator for enterprise bug report creation

**Implementation:**

* **New Tab:** "Bugs Enhancement Prompt" added alongside "Test Scenarios Generation"
* **Tab Switching:** Client-side only, toggles content panels with `.tab-panel` classes
* **State Preservation:** Inputs remain intact when switching tabs (no reset)

* **Bug Prompt Inputs (6 fields):**
  * Bug Title
  * Bug Description / Summary
  * Preconditions
  * Steps to Reproduce
  * Expected Result
  * Actual Result

* **Prompt Template (Immutable):**
  * Enterprise-grade bug report instructions and tone
  * Enforces strict section order with emoji headers
  * Output rules: no extra commentary, no meta text

* **Prompt Generation Logic:**
  * `generateBugPrompt()` embeds user input values into the fixed template
  * Empty fields injected as empty content (no validation)
  * Output rendered in read-only textarea with copy button

* **Copy Behavior:**
  * `copyBugPrompt()` uses the same clipboard logic and feedback animation
  * Inline "Copied to clipboard" feedback, no alert dialogs

#### 12. **UI and Prompt Refinements (Phase 8)**

**Change:** Polished the bug tab layout, removed the unused Bug Summary input, and aligned prompt outputs with user-specified counts and iconography.

**Implementation:**

* **Bug Tab UI Cleanup:**
  * Removed the commented Bug Summary field from the HTML form
  * Updated `generateBugPrompt()` to stop referencing `bug-summary`
  * Centered bug form content with a consistent max-width
  * Added soft input background and improved focus state
  * Full-width "Generate Bug Prompt" button for clarity

* **Bug Output Layout:**
  * Centered output section to match the main form
  * Improved spacing between textarea and buttons
  * Maintained full-width output textarea

* **Prompt Category Iconography:**
  * Injected emoji icons into the test case category list in the generated prompt
  * Icons include: Happy Path (✅), Negative/Validation (❌), Edge (⚠️), UI/UX (🎨), Navigation (🧭), Security (🔐), Performance (⏱️)

- **Dynamic Count Alignment:**
  - Test case count ranges are derived from the exact user input value
  - Ensures every section minimum is computed relative to the entered count
#### 13. **Workflow Logic (Checkboxes & Auto-Clear) (Phase 9)**
- **Change:** Added progress tracking to section titles and auto-reset logic for efficiency.
- **Implementation:**
  - Added disabled checkbox to each section title chip
  - **Auto-Check:** Copying a title programmatically checks its box
  - **Auto-Clear:** When all 7 checkboxes are checked, `story-title` and `story-desc` inputs are cleared automatically
  - **Layout:** optimized form grid and moved Copy/Preview buttons inline with Generate for better workflow
  
---

---

### Summary of Modifications

| Modification              | Type                | Impact                                         |
| ------------------------- | ------------------- | ---------------------------------------------- |
| Cairo font integration    | Enhancement         | Visual consistency, multilingual support       |
| Validation removal        | Bug Fix             | Unblocked UX, enabled partial input generation |
| Modern UI design          | Enhancement         | Professional appearance, improved UX           |
| Section titles generator  | New Feature         | Streamlined test category creation             |
| Enhanced prompt template  | Content Enhancement | Gazer-specific, comprehensive QA rules         |
| US prefix auto-removal    | New Feature         | Cleaner title generation                       |
| Modified Technology Input | New Feature         | Intelligent dropdown with 8 tech stacks        |
| Tech Badges               | New Feature         | Visual component breakdown                     |
| Platform-to-Tech Mapping  | New Feature         | Dynamic dropdown population                    |
| Default Tech Stack        | Enhancement         | Web + Angular-Laravel-MySQL pre-selected       |
| Bugs enhancement tab      | New Feature         | Dedicated bug report prompt generator          |
| Bug tab UI refinements    | Enhancement         | Centered layout, cleaner styling               |
| Bug Summary removal       | Bug Fix             | Removed unused field and prompt reference      |
| Prompt iconography        | Enhancement         | Emoji icons in category list                   |
| Dynamic count alignment   | Enhancement         | Section counts derived from user input         |
| Section Checkboxes        | New Feature         | Visual progress tracking for test generation   |
| Auto-Clear Logic          | New Feature         | Streamlined workflow for sequential stories    |
| Action Buttons Relocation | UX Enhancement      | Improved accessibility of key actions          |

**Status:** All modifications implemented and tested. System is fully operational and compliant with updated enterprise requirements.