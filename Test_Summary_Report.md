# 📊 TEST SUMMARY REPORT (TSR)

* **💼 Project Name:** Academy Practicum - Web Project QA
* **🖥️ System Under Test:** Web Application (QA-Staging Environment)
* **⏱️ Execution Period:** September 2026
* **📅 Report Date:** September 22, 2026
* **👤 Prepared By:** Dmitry Kravchenko (QA Engineer)
* **🔄 Execution Status:** ✅ COMPLETED
* **🚫 Release Gate:** ⛔ **REJECTED** (Quality Gate Failed due to open Blocker defect)

---

## 1. 🎯 PROJECT OVERVIEW & SCOPE
This testing cycle validated layout stability, responsive grid alignment, navigation workflows, and core functionality across 6 platform modules:

* 🏠 **[About Us Component]** (`aboutus.html`): Main headings, mission statements, corporate values cards, and accordion controls (Tests T274 - T285).
* 📖 **[Theory Module]** (`theory.html`): Handbook downloads, content hierarchy, and dynamic footer copyright year rendering (Tests T286 - T288).
* 🔍 **[Courses Catalog]** (`courses.html`): Course cards grid, search input queries, filter criteria, and sorting controls (Tests T289 - T305).
* 🛠️ **[Bugs & Test Cases Sandbox]** (`bugs.html`): Interactive board controls, bug form fields, execution filters, and report triggers (Tests T306 - T322).
* 👥 **[Team / Instructors Section]** (`aboutus.html` sub-module): Mentor profile cards, portrait hover overlay animations, and social links (Tests T323 - T341).
* 💎 **[Brand Identity Kit]** (`theory.html` sub-module): Media kit tokens, logo rendering, color code palettes, and resolution constraints (Tests T342 - T358).

**⛔ Out of Scope:**
* Landing intro revisions (`home.html` hero redesign).
* Career guides and external resource schemas (`interesting.html`).
* User registration form boundary validation (`register.html` submission flows).
* Test cases repository documentation view (`testcases.html`).

---

## 2. 📈 TEST METRICS & EXECUTION SUMMARY
**Execution metrics breakdown:**
* 🔢 **Total Test Cases Executed:** 85 (100.0%)
* ✅ **Passed Test Cases:** 82 (96.47%)
* ❌ **Failed Test Cases:** 3 (3.53%)
* ⏸️ **Blocked / Skipped Cases:** 0 (0.00%)

> **📊 Test Execution Success Rate (Pass Rate): 96.47%**
> **🎯 Quality Gate Minimum Compliance Target: 98.00%**

---

## 3. 🗂️ COMPREHENSIVE MODULE BREAKDOWN
**Distribution across executed modules:**

| Module | Scope | Total Tests | Results | Status |
| :--- | :--- | :--- | :--- | :--- |
| 🏠 **About Us Component** | T274 - T285 | 12 | 11 Passed, 1 Failed (#BUG-01) | 🟡 UNSTABLE |
| 📖 **Theory Handbook** | T286 - T288 | 3 | 3 Passed, 0 Failed | 🟢 STABLE |
| 🔍 **Courses Catalog** | T289 - T305 | 17 | 16 Passed, 1 Failed (#BUG-02) | 🔴 **FAILED** |
| 🛠️ **Bugs Sandbox** | T306 - T322 | 17 | 17 Passed, 0 Failed | 🟢 STABLE |
| 👥 **Team / Instructors** | T323 - T341 | 19 | 18 Passed, 1 Failed (#BUG-03) | 🟡 UNSTABLE |
| 💎 **Brand Identity Kit** | T342 - T358 | 17 | 17 Passed, 0 Failed | 🟢 STABLE |
| **Total Scope** | **T274 - T358** | **85** | **82 Passed, 3 Failed** | |

---

## 4. 🐛 DETAILED DEFECT LOG (FAILED TEST CASES)
**Traceability log for all logged defects:**

### 🏷️ Defect ID: #BUG-01 (T278)
* **📝 Summary:** Visual Layout Shift and Text Overlap in Corporate Values Area
* **📂 Module:** `aboutus.html` / Corporate Values Block
* **⚠️ Severity:** 🟡 Minor
* **📌 Priority:** 🔹 Low
* **🪜 Steps to Reproduce:**
1. Navigate to `aboutus.html`.
2. Scroll down to the Corporate Values section.
3. Inspect component alignment during DOM rendering.
* **🎯 Expected Result:** Corporate values cards render with proper padding and margins.
* **💥 Actual Result:** Value description text nodes (`.value-desc`) fail to position cleanly, causing partial overlap with adjacent card borders.

### 🏷️ Defect ID: #BUG-02 (T297)
* **📝 Summary:** Course Catalog Dynamic Search Filter Query Parsing Failure
* **📂 Module:** `courses.html` / Search Input Bar
* **⚠️ Severity:** 🔴 **Critical (Release Blocker)**
* **📌 Priority:** 🔺 High
* **🪜 Steps to Reproduce:**
1. Open the Courses Catalog (`courses.html`).
2. Focus on the dynamic search bar input field.
3. Type search string 'API'.
* **🎯 Expected Result:** Course catalog view updates dynamically to show 'API Testing'.
* **💥 Actual Result:** Grid fails to update dynamically upon query entry; unfiltered catalog view remains visible and matching card is not isolated.

### 🏷️ Defect ID: #BUG-03 (T337)
* **📝 Summary:** Hover State Transparency Overlay Inactive on Teacher Portrait
* **📂 Module:** `aboutus.html` / Instructor Card (Dmitry Kravchenko)
* **⚠️ Severity:** 🟡 Minor
* **📌 Priority:** 🔹 Low
* **🪜 Steps to Reproduce:**
1. Open the Team / Instructors section on `aboutus.html`.
2. Locate the mentor card for Dmitry Kravchenko.
3. Hover mouse cursor over the instructor portrait picture.
* **🎯 Expected Result:** Portrait darkens with opacity transition revealing social links.
* **💥 Actual Result:** CSS `:hover` state fails to trigger opacity layer; social link icons remain invisible and inaccessible to click events.

---

## 5. ⚖️ QUALITY ASSESSMENT & RELEASE RECOMMENDATION

🚦 **RELEASE GATE VERDICT:** ⛔ **REJECTED (Quality Gate Failed)**

**🔍 Quality Gate Criteria Compliance:**
* 📉 **Pass Rate Criteria:** Target >= 98.00% (Actual: 96.47% — ❌ FAILED)
* 🛑 **Blocker/Critical Defects:** Target = 0 (Actual: 1 Open Critical — ❌ FAILED)

📢 **Conclusion:**
Build v2026.9.22 cannot be deployed to Production. Broken search filtering (#BUG-02 / T297) restricts core course discovery journeys. Non-blocking UI bugs (#BUG-01 and #BUG-03) are deferred to the sprint backlog.

---

## 6. 🚀 RECOMMENDED ACTION PLAN & REGRESSION SCOPE

**💻 Development Engineering:**
* 🛠️ Fix search input keyup/change listener and filter logic in `courses.html`.
* 🎨 Patch CSS `:hover` pseudo-class overlay on mentor portrait wrappers in `aboutus.html`.
* 📐 Adjust DOM container margin and padding in Corporate Values cards in `aboutus.html`.

**🔁 Regression Test Scope (Hotfix Verification):**
* 🔄 Re-execute failed test cases: T278, T297, T337.
* 🧪 Validate dependent filter/pagination test cases: T292, T295, T296, T300, T304.
* 💨 Conduct sanity smoke run on `aboutus.html` and `courses.html`.

---
🏁 **END OF TEST SUMMARY REPORT** 🏁
