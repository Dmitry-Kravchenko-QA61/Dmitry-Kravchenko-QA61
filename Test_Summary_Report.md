# Test Summary Report: Web Application Functional & UI Verification

## 1. Project Overview

* **Project Name:** Academy Practicum — Web Project QA (QA Portfolio Validation Suite)
* **Environment:** Web Application (QA-Staging environment)
* **Testing Period:** September 2026
* **QA Engineer:** Dmitry Kravchenko

## 2. Objective & Scope

The primary focus of this testing cycle was scoped strictly to core modules of the web platform to verify layout stability, end-to-end navigation flows, and UI/UX layout positioning across desktop screen resolutions.

### In Scope:
* 📄 **About Us Page (aboutus.html):** Validation of main headings, mission blocks, corporate growth links, values layout, and accordion component behavior **(Tests T274 – T285)**.
* 📖 **Theory Website Module (theory.html):** Verification of layout elements, handbook document download link, and copyright year rendering **(Tests T286 – T288)**.
* 🔍 **Courses Catalog (courses.html):** Verification of grid layouts, search accuracy, dynamic sidebar filtering, and sorting behaviors **(Tests T289 – T305)**.
* 🛠 **Bugs & Test Cases Module (bugs.html):** Validation of the Kanban board drag-and-drop mechanics, mock bug tracking form fields, analytical grid rendering, case execution filtering, report export triggers, and error log simulators **(Tests T306 – T322)**.
* 👥 **Team / Instructors Section (theory.html - Shared Host):** Verification of expert profiles, filter tabs, modal biographies, teacher portrait hover states, skeleton loaders, and section counters **(Tests T323 – T341)**. *Note: Validated within the main theory page layout which structurally hosts this block.*
* 🔷 **Brand Identity Media Page (External Environment / CDN):** Validation of Media Kit parameters, brand logo assets, hex color tokens, and file size constraints **(Tests T342 – T358)**.

### Out of Scope (Deferred to Next Sprint):
* 🏠 **Home Page / Landing Interface (home.html):** Main introduction layout validation and baseline entry nodes (deferred due to pending design system revisions).
* 👤 **User Registration Flows (register.html):** Dedicated registration input form boundary conditions, field validation rules, error state triggers, and end-to-end data submission (except for the integration catalog redirect button check in T294).
* 📂 **Test Cases Management Hub (testcases.html):** Dedicated test documentation repository interface (completely deferred to the next sprint as no active test data or log history was recorded for this module in the current execution cycle).
* 💡 **Interesting Links Content Hub (interesting.html):** Static articles module and external resource referral redirects (excluded from the active testing scope by product team alignment).

---

## 3. Test Design & Metrics Summary

 A total of 85 manual test cases were executed. The test suite utilized core black-box techniques including equivalence partitioning (EP), boundary value analysis (BVA), and state transition testing to validate UI controls and functional boundaries.

### Execution Dashboard

| Total Executed | Passed | Failed | Blocked | Pass Rate |
| :---: | :---: | :---: | :---: | :---: |
| **85** | **82** | **3** | **0** | **96.47%** |

* 📈 **Passed (82):** Test cases executed successfully where the actual result matched the expected outcome.
* 📉 **Failed (3):** Critical deviations from requirements identified in T278 (Bug #1), T297 (Bug #2), and T337 (Bug #3).
* 🚫 **Blocked (0):** No test cases were blocked during this execution cycle.
* 🧮 **Pass Rate Calculation:** Passed / Total Executed — (82/85) * 100% = 96.47%.

### 3.1. Testing Caveats & Legacy Documentation Anomalies

During the test execution cycle, the QA team identified several logical discrepancies within the inherited test case documentation suite. To maintain metrics consistency across the active sprint, these cases were processed under the following parameters:

* 🌐 **Localization Constraints (Case T283):** Test case T283 contains a legacy requirement specifying a localization switch from "Russian to English". However, as documented in the active system specifications, the platform is fully localized in Ukrainian with no native Russian UI support implemented. Because the literal execution of the written steps was impossible, the status was evaluated as Passed solely in relation to the technical framework stability of the localization switch container interface component (tested via the available Ukrainian-to-English transition), rather than the outdated scenario steps. *Recommendation: Submit Case T283 for documentation refactoring to align with the active application architecture.*
* ⚡ **Performance Metric Verification (Case T286):** Case T286 mandates that the page must fully load in less than 2 seconds via manual verification. Since microsecond network layer shifts cannot be verified accurately with the naked eye, the execution status was benchmarked using the Chrome DevTools Network performance profiler (DOMContentLoaded and Finish metrics) to ensure objective validation before marking the test as Passed.
* 🔍 **Truncated Step Description (Case T288):** The implementation step for Case T288 abruptly terminates with an ellipsis ("Scroll to the bottom footer of the Theory page..."). The execution pass criteria were successfully inferred from the expected result column ("Footer shows correct current copyright year"), and full visual verification of the dynamic year rendering was completed.
* 📂 **Environment Discrepancy & Repository File Absence (Brand Asset Scope):** Test cases T342–T358 reference the "Brand Identity media page". Review of the local deployment package confirmed that no physical file named brand.html exists within the repository. To ensure testing continuity, validation of these 17 cases was redirected and executed against the live external environment (Staging CDN asset directory) as implied by the test case preconditions. Cases T338–T341 were executed natively within their designated module framework on the Team / Instructors section layout.

### 3.2. Module Distribution & Findings

| Module / Page | Test Case IDs | Total Tests | Passed | Failed | Status / Defects Found |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **About Us Page** | T274 – T285 | 12 | 11 | 1 | 🔴 **Bug #1 (Minor):** Corporate Values block causes minor visual layout shift (ID: T278). |
| **Theory Website Module** | T286 – T288 | 3 | 3 | 0 | ⚫ **Stable.** Layout elements, download links, and footer render properly. |
| **Courses Catalog** | T289 – T305 | 17 | 16 | 1 | 🔴 **Bug #2 (Critical):** Catalog search query parsing failure (ID: T297). |
| **Bugs & Test Cases Module** | T306 – T322 | 17 | 17 | 0 | ⚫ **Stable.** Kanban board drag-and-drop, form inputs, test grid filters, and report export controls passed. |
| **Team / Instructors Section** | T323 – T341 | 19 | 18 | 1 | 🔴 **Bug #3 (Minor):** Hover state transparency overlay blocks social links (ID: T337). |
| **Brand Identity Media Page** | T342 – T358 | 17 | 17 | 0 | ⚫ **Stable.** Asset wrappers, resolution badges, and hex copy-to-clipboard passed via external CDN deployment. |

---

## 4. Detailed Defect Logs (Discovered Bugs)

### 🐜 Bug #1: Visual Layout Shift on About Us Page (ID: T278)
* **Description:** The Corporate Values block causes a minor visual layout shift during standard DOM rendering, leading to a partial text overlap with adjacent components.
* **Severity:** Minor (UI Layout Discrepancy / Non-blocking).
* **Steps to Reproduce:**
  1. Navigate to the "About Us" page (`aboutus.html`).
  2. Scroll down to the Corporate Values section.
  3. Observe the structural component alignment during page render.
* **Actual Result:** Text blocks overlap with adjacent components during DOM rendering.
* **Expected Result:** Components are rendered with proper margins and zero padding overlaps.

### 🐜 Bug #2: Catalog Search Query Parsing Failure (ID: T297)
* **Description:** Typing specific search queries like 'API' into the course search bar does not dynamically update the catalog view grid. The 'API Testing' course card remains hidden, completely blocking users from finding matching content.
* **Severity:** Critical (Core Functional Restriction in Content Discovery).
* **Steps to Reproduce:**
  1. Open the Courses Catalog page (`courses.html`).
  2. Click on the dynamic search bar input box.
  3. Type the search query string "API".
* **Actual Result:** The view grid does not update; the 'API Testing' card remains completely hidden.
* **Expected Result:** Search results dynamically update to show 'API Testing' card.

### 🐜 Bug #3: Hover State Overlay Bug on Dmytro Kravchenko Portrait (ID: T337)
* **Description:** Hovering a cursor over the picture asset of Dmytro Kravchenko does not render the darkened opacity overlay correctly. As a result, the social sharing sub-elements remain partially hidden and unclickable, preventing users from interacting with the social media links.
* **Severity:** Minor (UI/UX Functionality Restriction).
* **Steps to Reproduce:**
  1. Open the dedicated **Team / Instructors** view page.
  2. Locate the instructor profile card for Dmytro Kravchenko.
  3. Hover the mouse cursor directly over Dmytro's background photo portrait.
* **Actual Result:** The darkened opacity overlay fails to trigger on this specific portrait; social links remain hidden and unclickable.
* **Expected Result:** The hover state instantly triggers the opacity overlay and renders accessible social media links.

## 5. Conclusion & Recommendations

While the overall platform architecture shows robust structural stability across most tested flows, the final Quality Gate status is currently **❌ REJECTED (Fixes Required)** pending the immediate resolution of the single critical release blocker identified in the Courses Catalog.

### 🛑 Critical Release Blocker (Hotfix Required)

1. **Bug #2 (Test Case T297):** Core functional restriction in dynamic course query parsing which completely breaks the search workflow.

### ➡️ Next Steps & Action Plan

1. **Immediate Hotfix Deployment:** A targeted hotfix deployment is strictly requested for the Courses Catalog module to resolve Bug #2 (T297). This defect introduces a critical behavior that fails to meet baseline deployment quality standards for the production environment and must be resolved before branch closure.
2. **Sprint Backlog Deferral:** The UI styling regressions tracked in Bug #1 (T278) and Bug #3 (isolated strictly to test case T337) cause layout and UX inconveniences but do not impact core business logic boundaries. These issues can be safely deferred to the next sprint backlog for post-release processing or concurrent maintenance.
3. **Regression Cycle Scheduling:** Once development delivers verified source patches for Bug #2 (T297), a targeted manual retest and full regression suite must be executed. This execution must cover the catalog search matrix, team card wrappers, and a sanity check on the deferred layout bugs to validate full Quality Gate compliance without side-effects.
