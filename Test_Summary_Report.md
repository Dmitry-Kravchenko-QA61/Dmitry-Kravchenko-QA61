# Test Summary Report: Web Application Functional & UI Verification

## 1. Project Overview

* **Project Name:** Academy Practicum — Web Project QA (QA Portfolio Validation Suite)
* **Environment:** Web Application (QA-Staging environment)
* **Testing Period:** September 2026
* **QA Engineer:** Dmitry Kravchenko

## 2. Objective & Scope

The primary objective of this testing cycle was to verify the functional and visual integrity of the QA Learning educational web platform, validate desktop responsiveness, and assess release readiness against baseline quality gates.

### In Scope (Delivered Repository Modules)
* **Theory Website Module (`theory.html`):** Validation of core layout elements, learning handbook document download trigger, copyright year rendering, and the embedded Team/Instructors Section (expert bio cards, profile state transitions, counters, and modal triggers) (Tests T286–T288, T323–T341).
* **Brand Assets Repository:** Verification of local static image assets (`Логотип для платформи QA Learning.png`) against platform specifications.

### Blocked Scope (Missing Repository Deliverables)
The following modules were planned in test design suite T274–T358 but could not be verified locally due to the absence of corresponding HTML deployment files in the repository package:
* **About Us Page (`aboutus.html`):** Tests T274–T285 (12 tests) — Blocked (Missing file).
* **Courses Catalog (`courses.html`):** Tests T289–T305 (17 tests) — Blocked (Missing file).
* **Bugs & Test Cases Module (`bugs.html`):** Tests T306–T322 (17 tests) — Blocked (Missing file).
* **Brand Identity Media Hub (`brand.html` / External asset archives):** Tests T342–T358 (17 tests) — Blocked (Dedicated page and downloadable vector packs missing from deployment).

### Uncovered Available Modules (Deferred to Dedicated Test Design Cycle)
The following components are present in the repository code base but lacked formal test cases in the inherited T274–T358 suite:
* **Home Page / Landing Interface (`home.html`):** Requires dedicated landing test design.
* **User Registration Flows (`register.html`):** Requires dedicated boundary value analysis (BVA) and equivalence partitioning (EP) suite.
* **Test Cases Management Hub (`testcases.html`):** Requires repository repository rendering verification.
* **Interesting Links Hub (`interesting.html`):** Requires link status and referral target audits.

---

## 3. Test Design & Metrics Summary

A suite of 85 formal test cases (T274–T358) was audited. Execution was strictly constrained to verifiable source files present within the deployment archive.

### Execution Dashboard

| Total Planned | Total Executed | Passed | Failed | Blocked | Pass Rate (Executed) | Coverage vs Target |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **85** | **23** | **22** | **1** | **62** | **95.65%** | **27.06%** |

* **Passed (22):** Test cases executed successfully within `theory.html` where actual results fully matched specifications.
* **Failed (1):** Defect identified in test case T337 (Bug #1).
* **Blocked (62):** Tests blocked due to missing deployment files (`aboutus.html`, `courses.html`, `bugs.html`, and `brand.html`).
* **Pass Rate Calculation:** Passed / Executed — (22 / 23) × 100% = 95.65%.

---

### 3.1. Testing Caveats & Documentation Anomalies

* **Localization Scenario Refactoring (Case T283):** Test case T283 mandates validating a localization switch from "Russian to English". The active application architecture is developed with Ukrainian as the native default language. Because literal execution of the legacy test step was impossible, the test was flagged as **Blocked / Needs Refactoring** rather than marked as Passed.
* **Performance Metric Verification (Case T286):** Page load validation was objectively benchmarked using Chrome DevTools Network performance profiler (measuring DOMContentLoaded and Finish metrics under network throttling).
* **Truncated Step Description (Case T288):** Step description terminates abruptly with an ellipsis; validation criteria were inferred and verified against the expected dynamic copyright year.
* **Team / Instructors Section Hosting Architecture:** Tests T323–T341 reference a standalone "Team / Instructors" page in preconditions. In the current build, this section is embedded within `theory.html`. Preconditions have been mapped accordingly.

---

### 3.2. Module Distribution & Findings

| Module / Scope | Test Case IDs | Planned | Executed | Passed | Failed | Blocked | Status / Defect Summary |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **About Us (`aboutus.html`)** | T274–T285 | 12 | 0 | 0 | 0 | 12 | **BLOCKED:** File missing from repository package. |
| **Theory Module (`theory.html`)** | T286–T288 | 3 | 3 | 3 | 0 | 0 | **STABLE:** Load metrics, handbook download link, and copyright render properly. |
| **Courses Catalog (`courses.html`)** | T289–T305 | 17 | 0 | 0 | 0 | 17 | **BLOCKED:** File missing from repository package. |
| **Bugs Sandbox (`bugs.html`)** | T306–T322 | 17 | 0 | 0 | 0 | 17 | **BLOCKED:** File missing from repository package. |
| **Team / Instructors (`theory.html`)** | T323–T341 | 19 | 19 | 18 | 1 | 0 | **DEFECT:** Bug #1 (UI Hover overlay visibility failure on portrait card). |
| **Brand Identity Scope** | T342–T358 | 17 | 1 | 1 | 0 | 16 | **PARTIALLY BLOCKED:** Local image verified; `brand.html` and bundles missing. |

---

## 4. Detailed Defect Logs

### Bug #1: Hover State Overlay Failure on Dmytro Kravchenko Portrait Card (ID: T337)
* **Severity:** Minor (UI/UX Functionality Glitch)
* **Priority:** Medium
* **Module:** `theory.html` (Team / Instructors Section)
* **Steps to Reproduce:**
  1. Open `theory.html` in a supported desktop browser.
  2. Navigate down to the "Mentors of QA Learning Ecosystem" section.
  3. Hover the mouse cursor directly over the portrait photo asset of instructor Dmytro Kravchenko.
* **Actual Result:** The darkened opacity overlay fails to trigger correctly; social follow icons remain inaccessible/unclickable.
* **Expected Result:** Hovering over the portrait activates the dark overlay and displays accessible, clickable social media links.

### Process Defect #1: Missing Core Platform Deliverables in Repository (Build Blocker)
* **Severity:** Critical (Release Blocker)
* **Priority:** High
* **Module:** Build & Repository Assembly
* **Description:** Deployment archive lacks core interface pages (`aboutus.html`, `courses.html`, `bugs.html`) required by specifications and QA test suites, preventing validation of 62 test cases.

---

## 5. Conclusion & Recommendations

The final Quality Gate status for the current sprint is **REJECTED (Fixes & Complete Build Required)**. 

While the delivered `theory.html` interface demonstrated robust structural stability (95.65% pass rate on executed tests), the release cannot proceed due to missing deployment files and blocked functional suites.

### Action Plan & Next Steps
1. **Repository Synchronization & Re-assembly (DevOps / Dev):**
   * Audit feature branches and integrate missing core files (`aboutus.html`, `courses.html`, `bugs.html`, `brand.html`) into the release branch.
   * Patch CSS hover pseudo-classes and z-index hierarchy for instructor card overlays (`theory.html`, Bug #1).
2. **Test Documentation Refactoring (QA Team):**
   * Refactor Case T283 to reflect Ukrainian-to-English localization switches.
   * Expand test design (EP/BVA) to cover previously untested pages (`register.html`, `home.html`, `testcases.html`, `interesting.html`).
3. **Execution of Full Regression Cycle:**
   * Schedule a complete verification run once the unified build package containing all platform modules is deployed.
