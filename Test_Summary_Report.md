# 📊 TEST SUMMARY REPORT (TSR)

* **💼 Project Name:** QA Learning Web Platform (Full-Stack QA Practicum)
* **🖥️ System Under Test:** QA Learning Web Platform & Backend API (QA Staging Environment)
* **📄 Document Identifier:** `TSR-QALEARN-2026-V1.0`
* **📋 Master Test Plan Ref:** `TP-QALEARN-2026-V1.0`
* **⏱️ Execution Period:** September 2026
* **📅 Report Date:** September 22, 2026
* **👤 Prepared By:** Dmitry Kravchenko (Junior QA Engineer)
* **🔄 Execution Status:** ✅ COMPLETED (100% Scope Executed)
* **🚫 Release Quality Gate:** ⛔ REJECTED (Quality Gate Failed — Release Blocked)

---

## 1. 🎯 PROJECT OVERVIEW & SCOPE
This testing cycle validated UI/UX architecture, client-server data exchange, relational SQL database integrity, and core functionality across 7 modules of the desktop version of the QA Learning Web Platform (1280px–1920px viewports):

* 🏠 **Corporate Overview** (`aboutus.html`): Main headings, corporate values cards DOM structure, FAQ accordion controls, language switcher toggle (Tests T274 – T285).
* 📖 **Handbook & Core Theory** (`theory.html`): Handbook PDF download integrity (HTTP 200 OK), page load speed (<1.2s), dynamic copyright year script (Tests T286 – T288).
* 🔍 **Course Search & Filtration** (`courses.html`): Catalog grid rendering, dynamic search bar query parsing, category/level filter logic, ascending price sorting (Tests T289 – T305).
* 🛠️ **Bug Tracker & Sandbox** (`bugs.html`): Kanban board drag-and-drop defect cards, form field client-side validation, mock test summary export, simulated 500 error handling (Tests T306 – T322).
* 👥 **Team & Mentors Directory** (`aboutus.html` sub-module): Mentor profile cards, detailed bio modal dialog with Escape key dismiss, desktop grid alignment (Tests T323 – T341).
* 💎 **Brand Identity & Media Kit** (`theory.html` sub-module): High-resolution brand bundle download (ZIP archive), Hex color tokens display, typography guidelines (Tests T342 – T352).
* 🔐 **User Registration & Database** (`register.html` / SQL): Form boundary validation (BVA), password complexity enforcement, BCrypt password hashing, and relational SQL database integrity (SELECT, INSERT, JOIN, WHERE, UNIQUE constraint) (Tests T353 – T358).

⛔ **Out of Scope:**
* Deferred web pages (`home.html` hero redesign, `testcases.html`, `interesting.html`).
* Mobile and tablet viewports (<1280px).
* Load, stress, and penetration testing.

---

## 2. 📈 TEST METRICS & EXECUTION SUMMARY

| Metric Parameter | Target Threshold | Actual Result | Variance | Status |
| :--- | :---: | :---: | :---: | :---: |
| **Total Test Cases Executed** | 85 (100% Scope) | **85** | 0 | ✅ Completed |
| **Passed Test Cases** | >= 83 | **82** | -1 | ⚠️ Review |
| **Failed Test Cases** | <= 2 | **3** | +1 | ❌ Exceeded |
| **Overall Test Suite Pass Rate** | >= 98.00% | **96.47% (96.5%)** | -1.53% | ❌ Failed |
| **Blocker / Critical Defects Open** | Exactly 0 | **1 Open (`BUG-02`)** | +1 | ❌ Blocker |
| **High Severity Defects Open** | <= 1 (Triaged) | **1 Open (`BUG-01`)** | 0 | ⚠️ Triaged |
| **Medium Severity Defects Open** | <= 2 | **1 Open (`BUG-03`)** | 0 | ✅ Acceptable |
| **Smoke Checklist Execution** | 100.0% Passed | **88.0% (22/25 Passed)** | -12.0% | ❌ Failed |

---

## 3. 🗂️ COMPREHENSIVE MODULE BREAKDOWN

| Module / Functional Area | Scope | Total Tests | Passed | Failed | Pass Rate | Defects Logged | Status |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 🏠 **Corporate Overview** | T274 – T285 | 12 | 11 | 1 | 91.7% | `BUG-01` (T278) | 🟡 UNSTABLE |
| 📖 **Handbook & Core Theory** | T286 – T288 | 3 | 3 | 0 | 100.0% | None | 🟢 STABLE |
| 🔍 **Course Search & Filtration** | T289 – T305 | 17 | 16 | 1 | 94.1% | `BUG-02` (T297) | 🔴 FAILED |
| 🛠️ **Bug Tracker & Sandbox** | T306 – T322 | 17 | 17 | 0 | 100.0% | None | 🟢 STABLE |
| 👥 **Team & Mentors Directory** | T323 – T341 | 19 | 18 | 1 | 94.7% | `BUG-03` (T337) | 🟡 UNSTABLE |
| 💎 **Brand Identity & Media Kit** | T342 – T352 | 11 | 11 | 0 | 100.0% | None | 🟢 STABLE |
| 🔐 **User Registration & Database** | T353 – T358 | 6 | 6 | 0 | 100.0% | None | 🟢 STABLE |
| **Total Scope** | **T274 – T358** | **85** | **82** | **3** | **96.5%** | **3 Defects** | ⛔ **REJECTED** |

---

## 4. 🐛 DETAILED DEFECT LOG (FAILED TEST CASES)

### 🏷️ Defect ID: BUG-01 (T278 / CHK-02)
* 📝 **Summary:** Visual Layout Shift and Text Overlap in Corporate Values Area
* 📂 **Module:** Corporate Overview (`aboutus.html`)
* ⚠️ **Severity:** High
* 📌 **Priority:** High
* 📋 **Steps to Reproduce:**
  1. Open Chrome/Firefox and navigate to `aboutus.html`.
  2. Scroll down to the Corporate Values cards section.
  3. Inspect DOM container rendering at 1280px and 1366px viewports.
* 🎯 **Expected Result:** Cards render with consistent internal padding and margins without overlapping borders.
* 💥 **Actual Result:** Text nodes inside `.value-desc` overflow container boundaries, overlapping adjacent card borders and violating WCAG spacing criteria.
* 🛠️ **Engineering Action:** Frontend team assigned to adjust CSS Flexbox wrapping (`flex-wrap: wrap`) and card margins.

### 🏷️ Defect ID: BUG-02 (T297 / CHK-10)
* 📝 **Summary:** Dynamic Course Search Query Parsing Failure (HTTP 400 Bad Request)
* 📂 **Module:** Course Search & Filtration (`courses.html`)
* ⚠️ **Severity:** Critical (Release Blocker)
* 📌 **Priority:** Highest
* 📋 **Steps to Reproduce:**
  1. Navigate to the Courses Catalog (`courses.html`).
  2. Focus on the dynamic search bar input field.
  3. Enter search string `'API'`.
* 🎯 **Expected Result:** API returns HTTP 200 OK with filtered results, dynamically displaying the 'API Testing' course card.
* 💥 **Actual Result:** Client-side regex parser triggers an unhandled exception resulting in HTTP 400 Bad Request response from `/api/v1/courses/search`. Catalog view freezes in loading state without displaying an error message.
* 🛠️ **Engineering Action:** Backend engineering hotfix required to sanitize query inputs and normalize uppercase string parsing.

### 🏷️ Defect ID: BUG-03 (T337 / CHK-21)
* 📝 **Summary:** CSS `:hover` Transparency Overlay Inactive on Mentor Portrait Cards
* 📂 **Module:** Team & Mentors Directory (`aboutus.html` sub-module)
* ⚠️ **Severity:** Medium
* 📌 **Priority:** Medium
* 📋 **Steps to Reproduce:**
  1. Navigate to the Team / Instructors section on `aboutus.html`.
  2. Hover cursor over the portrait card of Dmitry Kravchenko.
* 🎯 **Expected Result:** Card darkens with an animated opacity overlay (`opacity: 0.85`), revealing clickable LinkedIn and GitHub social link shortcuts.
* 💥 **Actual Result:** CSS `:hover` pseudo-class fails to trigger; social icons remain completely hidden and inaccessible to click events.
* 🛠️ **Engineering Action:** Add missing CSS transition rule and verify `z-index` stacking context on mentor card elements.

---

## 5. ⚖️ QUALITY ASSESSMENT & RELEASE RECOMMENDATION
🚦 **RELEASE QUALITY GATE VERDICT:** ⛔ **REJECTED (Release Blocked — Hotfixes Required)**

🔍 **Quality Gate Compliance Audit:**
* 📉 **Overall Test Suite Pass Rate:** Target >= 98.00% | Actual: **96.47% (96.5%)** — ❌ **FAILED**
* 🛑 **Blocker / Critical Defects:** Target = Exactly 0 Open | Actual: **1 Open (`BUG-02`)** — ❌ **FAILED**
* ⚠️ **High Severity Defects:** Target <= 1 Open (Triaged) | Actual: **1 Open (`BUG-01`)** — ⚠️ **TRIAGED**
* 📋 **Smoke Checklist Execution:** Target = 100.0% Passed | Actual: **88.0% Passed (22/25)** — ❌ **FAILED**

📢 **Conclusion:**
Target Build RC-1.0.4 cannot be deployed to Production. Broken search API parsing (`BUG-02`) blocks the core conversion funnel. Minor layout defect `BUG-01` and interactive CSS bug `BUG-03` require hotfixes prior to subsequent Quality Gate re-evaluation.

---

## 6. 🚀 RECOMMENDED ACTION PLAN & REGRESSION SCOPE

💻 **Development Engineering:**
* 🛠️ Deploy hotfix branch addressing search parameter casing for `/api/v1/courses/search` (`BUG-02`).
* 📐 Correct flex container padding and card margins in `aboutus.html` (`BUG-01`).
* 🎨 Patch CSS hover overlay transition on instructor cards (`BUG-03`).

🔁 **QA Regression Scope (Hotfix Verification):**
* 🔄 Re-execute failed manual test cases: `T278`, `T297`, `T337`.
* 💨 Execute full 25-point smoke checklist (`QA_Learning_Platform_25_Point_Checklist.xlsx`) to confirm 100% availability.
* 🧪 Perform targeted regression across catalog filtering and pagination scenarios: `T289`–`T305`.
* ⚖️ Re-evaluate Quality Gate criteria on Release Candidate RC-1.0.5.

***
🏁 **END OF TEST SUMMARY REPORT** 🏁
