# 📊 TEST SUMMARY REPORT (TSR)

*   **💼 Project Name:** QA Learning Platform (Full-Stack QA Practicum)
*   **🖥️ System Under Test:** QA Learning Web Platform & Backend API (QA-Staging Environment)
*   **⏱️ Execution Period:** September 2026
*   **📅 Report Date:** September 22, 2026
*   **👤 Prepared By:** Dmitry Kravchenko (QA Engineer)
*   **🔄 Execution Status:** ✅ COMPLETED
*   **🚫 Release Gate:** ⛔ REJECTED (Quality Gate Failed due to open Blocker defect)

---

## 1. 🎯 PROJECT OVERVIEW & SCOPE
This testing cycle validated UI architecture, client-server data exchange, relational database integrity (via SQL), and core functionality across 7 modules of the QA Learning educational web platform:

*   🏠 **Corporate Overview** (`aboutus.html`): Main headings, corporate values cards, and accordion controls (Tests T274 – T285).
*   📖 **Handbook & Core Theory** (`theory.html`): Handbook downloads, page load speed, and dynamic copyright year handling (Tests T286 – T288).
*   🔍 **Course Search & Filtration** (`courses.html`): Course cards grid, backend API search queries, database filter criteria, and sorting (Tests T289 – T305).
*   🛠️ **Bug Tracker & Sandbox** (`bugs.html`): Interactive board controls, form field validation, and database submission triggers (Tests T306 – T322).
*   👥 **Team & Mentors Directory** (`aboutus.html` sub-module): Mentor profile bio cards, database-driven bio rendering, and social links (Tests T323 – T341).
*   💎 **Brand Identity & Media Kit** (`theory.html` sub-module): Media kit tokens, logo rendering, and resolution constraints (Tests T342 – T352).
*   🔐 **User Registration & Database** (`register.html` / SQL): Form boundary validation, password hashing, and relational SQL database integrity (SELECT, INSERT, JOIN, WHERE) (Tests T353 – T358).

⛔ **Out of Scope:**
*   Landing intro revisions (`home.html` hero redesign).
*   Career guides and external resource schemas (`interesting.html`).
*   Test cases repository documentation view (`testcases.html`).

---

## 2. 📈 TEST METRICS & EXECUTION SUMMARY
Execution metrics breakdown:

*   🔢 **Total Test Cases Executed:** 85 (100.0%)
*   ✅ **Passed Test Cases:** 82 (96.47%)
*   ❌ **Failed Test Cases:** 3 (3.53%)
*   ⏸️ **Blocked / Skipped Cases:** 0 (0.00%)
*   📊 **Test Execution Success Rate (Pass Rate):** 96.47%
*   🎯 **Quality Gate Minimum Compliance Target:** 98.00%

---

## 3. 🗂️ COMPREHENSIVE MODULE BREAKDOWN
Distribution across executed modules:

| Module | Scope | Total Tests | Results | Status |
| :--- | :--- | :--- | :--- | :--- |
| 🏠 **Corporate Overview** | T274 – T285 | 12 | 11 Passed, 1 Failed (#BUG-01) | 🟡 UNSTABLE |
| 📖 **Handbook & Core Theory** | T286 – T288 | 3 | 3 Passed, 0 Failed | 🟢 STABLE |
| 🔍 **Course Search & Filtration** | T289 – T305 | 17 | 16 Passed, 1 Failed (#BUG-02) | 🔴 FAILED |
| 🛠️ **Bug Tracker & Sandbox** | T306 – T322 | 17 | 17 Passed, 0 Failed | 🟢 STABLE |
| 👥 **Team & Mentors Directory** | T323 – T341 | 19 | 18 Passed, 1 Failed (#BUG-03) | 🟡 UNSTABLE |
| 💎 **Brand Identity & Media Kit** | T342 – T352 | 11 | 11 Passed, 0 Failed | 🟢 STABLE |
| 🔐 **User Registration & Database** | T353 – T358 | 6 | 6 Passed, 0 Failed | 🟢 STABLE |
| **Total Scope** | **T274 – T358** | **85** | **82 Passed, 3 Failed** | ⛔ REJECTED |

---

## 4. 🐛 DETAILED DEFECT LOG (FAILED TEST CASES)
Traceability log for all logged defects:

### 🏷️ Defect ID: #BUG-01 (T278)
*   📝 **Summary:** Visual Layout Shift and Text Overlap in Corporate Values Area
*   📂 **Module:** `aboutus.html` / Corporate Values Block
*   ⚠️ **Severity:** 🟡 Minor
*   📌 **Priority:** 🔹 Low
*   📋 **Steps to Reproduce:**
1. Navigate to `aboutus.html`.
2. Scroll down to the Corporate Values section.
3. Inspect component alignment during DOM rendering.
*   🎯 **Expected Result:** Corporate values cards render with proper padding and margins.
*   💥 **Actual Result:** Value description text nodes (`.value-desc`) fail to position cleanly, causing partial overlap with adjacent card borders.

### 🏷️ Defect ID: #BUG-02 (T297)
*   📝 **Summary:** Course Catalog Dynamic Search Filter Query Parsing Failure
*   📂 **Module:** `courses.html` / Search Input Bar
*   ⚠️ **Severity:** 🔴 Critical (Release Blocker)
*   📌 **Priority:** 🔺 High
*   📋 **Steps to Reproduce:**
1. Open the Courses Catalog (`courses.html`).
2. Focus on the dynamic search bar input field.
3. Type search string 'API'.
*   🎯 **Expected Result:** Database query executes successfully and course catalog view updates dynamically to show 'API Testing'.
*   💥 **Actual Result:** Grid fails to update dynamically upon query entry; unfiltered catalog view remains visible and API response returns a 400 Bad Request error.

### 🏷️ Defect ID: #BUG-03 (T337)
*   📝 **Summary:** Hover State Transparency Overlay Inactive on Teacher Portrait
*   📂 **Module:** `aboutus.html` / Instructor Card (Dmitry Kravchenko)
*   ⚠️ **Severity:** 🟡 Minor
*   📌 **Priority:** 🔹 Low
*   📋 **Steps to Reproduce:**
1. Open the Team / Instructors section on `aboutus.html`.
2. Locate the mentor card for Dmitry Kravchenko.
3. Hover mouse cursor over the instructor portrait picture.
*   🎯 **Expected Result:** Portrait darkens with opacity transition revealing social links.
*   💥 **Actual Result:** CSS `:hover` state fails to trigger opacity layer; social link icons remain invisible and inaccessible to click events.

---

## 5. ⚖️ QUALITY ASSESSMENT & RELEASE RECOMMENDATION
🚦 **RELEASE GATE VERDICT:** ⛔ **REJECTED (Quality Gate Failed)**

🔍 **Quality Gate Criteria Compliance:**
*   📉 **Pass Rate Criteria:** Target >= 98.00% (Actual: 96.47% — ❌ FAILED)
*   🛑 **Blocker/Critical Defects:** Target = 0 (Actual: 1 Open Critical — ❌ FAILED)

📢 **Conclusion:**
Build v2026.9.22 of QA Learning Platform cannot be deployed to Production. Broken search filtering API response (#BUG-02 / T297) restricts core course discovery journeys. Non-blocking UI bugs (#BUG-01 and #BUG-03) are deferred to the sprint backlog.

---

## 6. 🚀 RECOMMENDED ACTION PLAN & REGRESSION SCOPE

💻 **Development Engineering:**
*   🛠️ Fix database query routing and API endpoint connection for the search filter in `courses.html`.
*   🎨 Patch CSS `:hover` pseudo-class overlay on mentor portrait wrappers in `aboutus.html`.
*   📐 Adjust DOM container margin and padding in Corporate Values cards in `aboutus.html`.

🔁 **Regression Test Scope (Hotfix Verification):**
*   🔄 Re-execute failed test cases: T278, T297, T337.
*   🧪 Validate dependent backend filter/pagination API tests: T292, T295, T296, T300, T304.
*   💨 Conduct sanity smoke run on DB connections for `register.html` and `courses.html`.

***
🏁 **END OF TEST SUMMARY REPORT** 🏁
