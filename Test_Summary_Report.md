# Test Summary Report: Web Application Functional & UI Verification

## 1. Project Overview

* **Project Name:** Academy Practicum — Web Project QA (QA Portfolio Validation Suite)
* **Environment:** Web Application (QA-Staging environment)
* **Testing Period:** September 2026
* **QA Engineer:** Dmitry Kravchenko

## 2. Objective & Scope

The primary focus of this testing cycle was scoped strictly to core modules of the web platform to verify layout stability, end-to-end navigation flows, and UI/UX layout positioning across desktop screen resolutions.

### In Scope:
* 📄 **About Us Page (aboutus.html):** Validation of main headings, mission blocks, corporate growth links, values layout, and accordion component behavior (**Tests T274 – T285**).
* 📘 **Theory Website Module (theory.html):** Verification of layout elements, handbook document download link, and copyright year rendering (**Tests T286 – T288**).
* 🔍 **Courses Catalog (courses.html):** Verification of grid layouts, search accuracy, dynamic sidebar filtering, and sorting behaviors (**Tests T289 – T305**).
* 🛠️ **Bugs Sandbox Module (bugs.html):** Validation of the Kanban board drag-and-drop mechanics, mock form fields data entry, and error log simulators (**Tests T306 – T315**).
* 👥 **Test Cases Hub Module (testcases.html):** Validation of test run execution status filter controls, analytical grid rendering, and report export triggers (**Tests T316 – T322**).
* 🤝 **Team / Instructors Module (theory.html):** Verification of expert profiles, filter tabs, modal biographies, and hover state interactions inside the team section (**Tests T323 – T341**).
* 🏷️ **Brand Identity Media Page (brand.html):** Validation of Media Kit parameters, brand logo assets, hex color tokens, and file size constraints (**Tests T342 – T358**).

### Out of Scope (Deferred to Next Sprint):
* 🏠 **Home Page / Landing Interface (home.html):** Main introduction layout validation and baseline entry nodes.
* 🔐 **User Registration Flows (register.html):** Dedicated registration input form boundary conditions, field validation rules, error state triggers, and end-to-end data submission (except for the integration catalog redirect button check in T294).

## 3. Test Design & Metrics Summary

A total of 85 manual test cases were executed. The test suite utilized core black-box techniques including equivalence partitioning (EP), boundary value analysis (BVA), and state transition testing to validate UI controls and functional boundaries.

### Execution Dashboard

| Total Executed | Passed | Failed | Blocked | Pass Rate |
| :---: | :---: | :---: | :---: | :---: |
| 85 | 82 | 3 | 0 | 96.47% |

### 3.1. Testing Caveats & Legacy Documentation Anomalies

During the test execution cycle, the QA team identified several logical discrepancies within the inherited test case documentation suite. To maintain metrics consistency across the active sprint, these cases were processed under the following strict parameters:

* **Localization Constraints (Case T283):** The test step references changing localization from *"Russian to English"*. However, as documented in the system specifications, the platform is **fully localized in Ukrainian** with no native Russian UI support implemented. The test was executed and marked as *Passed* based on the successful validation of the active Ukrainian-to-English localization switch container behavior.
* **Performance Metric Verification (Case T286):** Case T286 mandates that the page must fully load in *less than 2 seconds* via manual verification. Since microsecond network layer shifts cannot be verified accurately with the naked eye, the execution status was benchmarked using the Chrome DevTools Network performance profiler (DOMContentLoaded and Finish metrics) to ensure objective validation before marking the test as *Passed*.
* **Trunctuated Step Description (Case T288):** The implementation step for Case T288 abruptly terminates with an ellipsis (*"Scroll to the bottom footer of the Theory page..."*). The execution pass criteria were successfully inferred from the expected result column (*"Footer shows correct current copyright year"*), and full visual verification of the dynamic year rendering was completed.

### Module Distribution & Findings

| Module / Page | Test Case IDs | Total Tests | Passed | Failed | Status / Defects Found |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **About Us Page** | T274 – T285 | 12 | 11 | 1 | 🔴 **Bug #1 (Minor):** Corporate Values block causes minor visual layout shift. |
| **Theory Website Module** | T286 – T288 | 3 | 3 | 0 | 🟢 Stable. Layout elements, download links, and footer render properly. |
| **Courses Catalog** | T289 – T305 | 17 | 16 | 1 | 🔴 **Bug #2 (Critical):** Catalog search query parsing failure. |
| **Bugs Sandbox Module** | T306 – T315 | 10 | 10 | 0 | 🟢 Stable. Kanban board drag-and-drop and mock form validations passed. |
| **Test Cases Hub Module** | T316 – T322 | 7 | 7 | 0 | 🟢 Stable. Status filters and grid layouts rendering as intended. |
| **Team / Instructors Module** | T323 – T341 | 19 | 18 | 1 | 🔴 **Bug #3 (Minor):** Hover state transparency overlay blocks social links. |
| **Brand Identity Media Page** | T342 – T358 | 17 | 17 | 0 | 🟢 Stable. Asset wrappers and hex copy-to-clipboard passed. |

## 4. Detailed Defect Logs (Discovered Bugs)

### 🐛 Bug #1: Visual Layout Shift on About Us Page (ID: T278)

* **Description:** The Corporate Values block causes a minor visual layout shift during standard DOM rendering, leading to a partial text overlap with adjacent components.
* **Severity:** Minor (UI Layout Discrepancy / Non-blocking)
* **Steps to Reproduce:**
1. Navigate to the "About Us" page (aboutus.html).
2. Scroll down to the Corporate Values section.
3. Observe the structural component alignment during page render.
* **Actual Result:** Text blocks overlap with adjacent components during DOM rendering.
* **Expected Result:** Components are rendered with proper margins and zero padding overlaps.

### 🐛 Bug #2: Catalog Search Query Parsing Failure (ID: T297)

* **Description:** Typing specific search queries like 'API' into the course search bar does not dynamically update the catalog view grid. The 'API Testing' course card remains hidden, completely blocking users from finding matching content.
* **Severity:** Critical (Core Functional Restriction in Content Discovery)
* **Steps to Reproduce:**
1. Open the Courses Catalog page (courses.html).
2. Click on the dynamic search bar input box.
3. Type the search query string "API".
* **Actual Result:** The view grid does not update; the 'API Testing' card remains completely hidden.
* **Expected Result:** Search results dynamically update to show 'API Testing' card.

### 🐛 Bug #3: Hover State Overlay Bug on Team / Instructors Module (ID: T337)

* **Description:** Hovering a cursor over a Team / Instructor profile card background photo does not render the darkened opacity overlay correctly. As a result, the social sharing sub-elements remain partially hidden and unclickable, preventing users from interacting with the social media links.
* **Severity:** Minor (UI/UX Functionality Restriction)
* **Steps to Reproduce:**
1. Open the Theory page (theory.html).
2. Scroll down to the "Mentors of QA Learning Ecosystem" (Team / Instructors) section.
3. Locate the instructor profile card for Dmytro Kravchenko.
4. Hover the mouse cursor directly over the instructor's background photo.
* **Actual Result:** The darkened opacity overlay fails to trigger, leaving social links hidden and unclickable.
* **Expected Result:** The hover state instantly triggers the opacity overlay and renders accessible social media links.

## 5. Conclusion & Recommendations

While the overall platform architecture shows robust structural stability across most tested flows, the final Quality Gate status is currently **❌ REJECTED (Fixes Required)** pending the immediate resolution of the single critical release blocker identified in the Courses Catalog.

### 🛑 Critical Release Blocker (Hotfix Required)

1. **Bug #2 (Test Case T297):** Core functional restriction in dynamic course query parsing which completely breaks the search workflow.

### ➡️ Next Steps & Action Plan

1. **Immediate Hotfix Deployment:** A targeted hotfix deployment is strictly requested for the Courses Catalog module to resolve Bug #2 (T297). This defect introduces a critical behavior that fails to meet baseline deployment quality standards for the production environment and must be resolved before branch closure.
2. **Sprint Backlog Deferral:** The UI styling regressions tracked in Bug #1 (T278) and Bug #3 (T337) cause layout and UX inconveniences but do not impact core business logic boundaries. These issues can be safely deferred to the next sprint backlog for post-release processing or concurrent maintenance.
3. **Regression Cycle Scheduling:** Once development delivers verified source patches for Bug #2 (T297), a targeted manual retest and full regression suite must be executed. This execution must cover the catalog search matrix, team card wrappers, and a sanity check on the deferred layout bugs to validate full Quality Gate compliance without side-effects.
