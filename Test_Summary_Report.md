# 📊 TEST SUMMARY REPORT (TSR) 📋

* 📁 **Project Name:** Academy Practicum - Web Project QA
* 🖥️ **System Under Test:** Web Application (QA-Staging Environment)
* 🧩 **Modules Covered:** 🏠 Home / About Us (`home.html`), 📖 Theory Handbooks (`theory.html`), 🔍 Courses Catalog (`courses.html`), 🛠️ Interactive Sandbox (`interesting.html`), 👥 Instructors Directory (`theory.html`), 💎 Brand Identity Media Kit (brand assets)
* ⏱️ **Execution Period:** September 2026
* 📅 **Report Date:** September 22, 2026
* 👤 **Prepared By:** Dmitry Kravchenko (QA Engineer)
* 🔄 **Execution Status:** ✅ COMPLETED
* 🚫 **Release Gate:** ⛔ REJECTED (Quality Gate Failed due to open Blocker defect)
================================================================================

1. 🎯 PROJECT OVERVIEW & SCOPE
This testing cycle validated layout stability, responsive grid alignment, 
navigation workflows, and core functionality across 6 platform modules:

* 🏠 [About Us Component] (home.html): Main headings, mission statements, corporate 
  values cards, and accordion controls (Tests T274 - T285).
* 📖 [Theory Module] (theory.html): Handbook downloads, content hierarchy, and 
  dynamic footer copyright year rendering (Tests T286 - T288).
* 🔍 [Courses Catalog] (courses.html): Course cards grid, search input queries, 
  filter criteria, and sorting controls (Tests T289 - T305).
* 🛠️ [Bugs & Test Cases Sandbox] (interesting.html): Interactive board controls, 
  bug form fields, execution filters, and report triggers (Tests T306 - T322).
* 👥 [Team / Instructors Section] (theory.html shared host): Mentor profile cards, 
  portrait hover overlay animations, and social links (Tests T323 - T341).
* 💎 [Brand Identity Kit] (assets repository): Media kit tokens, logo rendering, 
  color code palettes, and resolution constraints (Tests T342 - T358).

⛔ Out of Scope:
* 🏠 Landing intro revisions (home.html hero redesign).
* 👤 User registration form boundary validation (register.html submission flows).
* 📑 Test cases repository documentation view (testcases.html).

2. 📈 TEST METRICS & EXECUTION SUMMARY
--------------------------------------------------------------------------------
Execution metrics breakdown:

* 🔢 Total Test Cases Executed : 85   (100.0%)
* ✅ Passed Test Cases         : 82   ( 96.47%)
* ❌ Failed Test Cases         : 3    (  3.53%)
* ⏸️ Blocked / Skipped Cases   : 0    (  0.00%)

[ 📊 Test Execution Success Rate (Pass Rate) : 96.47% ]
[ 🎯 Quality Gate Minimum Compliance Target  : 98.00% ]

3. 🗂️ COMPREHENSIVE MODULE BREAKDOWN
--------------------------------------------------------------------------------
Distribution across executed modules:

* 🏠 [About Us Component] (home.html)
  * 📋 Scope: T274 - T285 (Total: 12)
  * 📊 Results: 11 Passed, 1 Failed (Bug #1 / T278)
  * ⚠️ Status: 🟡 UNSTABLE (Minor layout overlap)

* 📖 [Theory Handbook Module] (theory.html)
  * 📋 Scope: T286 - T288 (Total: 3)
  * 📊 Results: 3 Passed, 0 Failed
  * 🛡️ Status: 🟢 STABLE

* 🔍 [Courses Catalog Workspace] (courses.html)
  * 📋 Scope: T289 - T305 (Total: 17)
  * 📊 Results: 16 Passed, 1 Failed (Bug #2 / T297)
  * 🛑 Status: 🔴 BLOCKED (Critical search parsing defect)

* 🛠️ [Bugs & Test Cases Sandbox] (interesting.html)
  * 📋 Scope: T306 - T322 (Total: 17)
  * 📊 Results: 17 Passed, 0 Failed
  * 🛡️ Status: 🟢 STABLE

* 👥 [Team / Instructors Section] (theory.html)
  * 📋 Scope: T323 - T341 (Total: 19)
  * 📊 Results: 18 Passed, 1 Failed (Bug #3 / T337)
  * ⚠️ Status: 🟡 UNSTABLE (Hover overlay styling failure)

* 💎 [Brand Identity Media Kit] (Brand Assets)
  * 📋 Scope: T342 - T358 (Total: 17)
  * 📊 Results: 17 Passed, 0 Failed
  * 🛡️ Status: 🟢 STABLE

🔢 Total Tests: 12 + 3 + 17 + 17 + 19 + 17 = 85 Test Cases.

## 4. 🐛 DETAILED DEFECT LOG (FAILED TEST CASES)

Traceability log for all logged defects:

---

### 🏷️ Defect ID: #BUG-01 (T278)
* 📝 **Summary:** Visual Layout Shift and Text Overlap in Corporate Values Area
* 📂 **Module:** `home.html` / Corporate Values Block
* ⚠️ **Severity:** 🟡 Minor
* 📌 **Priority:** 🔹 Low
* 🪜 **Steps to Reproduce:**
  1. Navigate to `home.html`.
  2. Scroll down to the Corporate Values section.
  3. Inspect component alignment during DOM rendering.
* 🎯 **Expected Result:** Corporate values cards render with proper padding and margins.
* 💥 **Actual Result:** Value description text nodes (`.value-desc`) fail to position cleanly, causing partial overlap with adjacent card borders.

---

### 🏷️ Defect ID: #BUG-02 (T297)
* 📝 **Summary:** Course Catalog Dynamic Search Filter Query Parsing Failure
* 📂 **Module:** `courses.html` / Search Input Bar
* ⚠️ **Severity:** 🔴 Critical (Release Blocker)
* 📌 **Priority:** 🔺 High
* 🪜 **Steps to Reproduce:**
  1. Open the Courses Catalog (`courses.html`).
  2. Focus on the dynamic search bar input field.
  3. Type search string `'API'`.
* 🎯 **Expected Result:** Course catalog view updates dynamically to show 'API Testing'.
* 💥 **Actual Result:** Grid fails to update dynamically upon query entry; unfiltered catalog view remains visible and matching card is not isolated.

---

### 🏷️ Defect ID: #BUG-03 (T337)
* 📝 **Summary:** Hover State Transparency Overlay Inactive on Teacher Portrait
* 📂 **Module:** `theory.html` / Instructor Card (Dmytro Kravchenko)
* ⚠️ **Severity:** 🟡 Minor
* 📌 **Priority:** 🔹 Low
* 🪜 **Steps to Reproduce:**
  1. Open the Team / Instructors section on `theory.html`.
  2. Locate the mentor card for Dmytro Kravchenko.
  3. Hover mouse cursor over the instructor portrait picture.
* 🎯 **Expected Result:** Portrait darkens with opacity transition revealing social links.
* 💥 **Actual Result:** CSS `:hover` state fails to trigger opacity layer; social link icons remain invisible and inaccessible to click events.

--------------------------------------------------------------------------------

5. ⚖️ QUALITY ASSESSMENT & RELEASE RECOMMENDATION
--------------------------------------------------------------------------------
🚦 RELEASE GATE VERDICT: ⛔ REJECTED (Quality Gate Failed)

🔍 Quality Gate Criteria Compliance:
* 📉 Pass Rate Criteria: Target >= 98.00% (Actual: 96.47% — ❌ FAILED)
* 🛑 Blocker/Critical Defects: Target = 0 (Actual: 1 Open Critical — ❌ FAILED)

📢 Conclusion:
Build v2026.9.22 cannot be deployed to Production. Broken search filtering 
(#BUG-02 / T297) restricts core course discovery journeys. Non-blocking UI bugs 
(#BUG-01 and #BUG-03) are deferred to the post-release sprint backlog.

6. 🚀 RECOMMENDED ACTION PLAN & REGRESSION SCOPE
--------------------------------------------------------------------------------
1. 💻 Development Engineering:
   * 🛠️ Fix search input keyup/change listener and filter logic in courses.html.
   * 🎨 Patch CSS :hover pseudo-class overlay on mentor portrait wrappers.
   * 📐 Adjust DOM container margin and padding in Corporate Values cards.

2. 🔁 Regression Test Scope (Hotfix Verification):
   * 🔄 Re-execute failed test cases: T278, T297, T337.
   * 🧪 Validate dependent filter/pagination test cases: T292, T295, T296, T300, T304.
   * 💨 Conduct sanity smoke run on home.html, courses.html, and theory.html.

================================================================================
                     🏁 END OF TEST SUMMARY REPORT 🏁
================================================================================
