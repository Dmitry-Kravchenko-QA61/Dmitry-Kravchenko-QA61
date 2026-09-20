# 📊 Test Summary Report: Web Application Functional & UI Validation

## 1. Project Overview

*   **Project Name:** Academy Practicum — QA Portfolio Validation Suite
*   **Environment:** Web Application (QA-Staging environment)
*   **Testing Period:** September 2026
*   **QA Engineer:** Dmitry Kravchenko

---

## 2. Objective & Scope

The primary focus of this testing cycle was scoped strictly to **5 core modules** of the web platform to verify layout stability, end-to-end navigation flows, and UI/UX layout positioning across desktop screen resolutions.

### In Scope:
*   📖 **Theory Website Module:** Validation of core headings, mission blocks, localization, and "accordion" behavior.
*   🔍 **Courses Catalog:** Verification of grid layouts, search accuracy, dynamic sidebar filtering, and sorting behaviors.
*   🐛 **Bugs & Test Cases:** Validation of the Kanban board drag-and-drop mechanics, mock form fields data entry, and error log simulators.
*   👥 **Team & Instructors:** Verification of expert profiles, filter tabs, modal biographies, and cross-browser desktop grid layout verification.
*   🎨 **Brand Identity Media Page:** Validation of Media Kit parameters, brand logo assets validation, technical spacing, hex color tokens, and vector file size constraints.

### Out of Scope (Deferred to Next Sprint):
*   **Home Page / Landing Interface:** Main introduction layout validation and baseline entry nodes.
*   **About Us Page:** Corporate profile statistics grid verification and historical timeline layout blocks.
*   **User Registration & Test Cases Hub:** Input form boundary conditions, field validation rules, error state triggers, and end-to-end data submission.

---

## 3. Test Design & Metrics Summary

A total of 85 manual test cases were executed. The test suite utilized core black-box techniques including equivalence partitioning (EP), boundary value analysis (BVA), and state transition testing to validate UI controls and functional boundaries.

### 📈 Execution Dashboard

| Total Executed | Passed | Failed | Blocked | Pass Rate |
| :---: | :---: | :---: | :---: | :---: |
| 85 | 82 | 3 | 0 | **96.47%** |

### ⚙️ Module Distribution & Findings

| Module / Page | Test Case IDs | Total Tests | Passed | Failed | Status / Defects Found |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Theory Website Module** | T274 – T288 | 15 | 14 | 1 | 🟡 **T278 Failed:** Corporate Values block causes minor visual layout shift. |
| **Courses Catalog** | T289 – T305 | 17 | 16 | 1 | 🔴 **T297 Failed (Critical):** Catalog search query parsing failure. |
| **Bugs & Test Cases** | T306 – T322 | 17 | 17 | 0 | 🟢 **Stable.** All mock Jira form controls working as intended. |
| **Team / Instructors** | T323 – T341 | 19 | 18 | 1 | 🔴 **T337 Failed (Critical):** Hover state overlay blocks social links. |
| **Brand Identity Media Page** | T342 – T358 | 17 | 17 | 0 | 🟢 **Stable.** Asset wrappers and hex copy-to-clipboard passed. |

---

## 4. Detailed Defect Logs (Discovered Bugs)

### 🐛 Bug #1: Visual Layout Shift on Theory Website Module (ID: T278)

*   **Description:** The Corporate Values block causes a minor visual layout shift during standard DOM rendering, leading to a partial text overlap with adjacent components.
*   **Severity:** Minor (UI Layout Discrepancy / Non-blocking)
*   **Steps to Reproduce:**
    1. Navigate to the Theory Website Module page.
    2. Scroll down to the "Corporate Values" section.
    3. Observe the structural component alignment.
*   **Actual Result:** Text blocks overlap with adjacent components during DOM rendering.
*   **Expected Result:** Components are rendered with proper margins and zero padding overlaps.

---

### 🐛 Bug #2: Catalog Search Query Parsing Failure (ID: T297)

*   **Description:** Typing specific search queries like 'API' into the course search bar does not dynamically update the catalog view grid. The 'API & DB Testing' course card remains hidden, completely blocking users from finding matching content.
*   **Severity:** Critical (Core Functional Restriction in Content Discovery)
*   **Steps to Reproduce:**
    1. Open the Courses Catalog page.
    2. Click on the dynamic search bar input box.
    3. Type the search query string "API".
*   **Actual Result:** View grid does not update; "API & DB Testing" card remains completely hidden.
*   **Expected Result:** Search query is parsed instantly, and all matching course cards are displayed dynamically.

---

### 🐛 Bug #3: Hover State Overlay Bug on Team / Instructors Module (ID: T337)

*   **Description:** Hovering a cursor over a mentor profile card background photo does not render the darkened opacity overlay correctly. As a result, the social sharing sub-elements remain hidden and unclickable, preventing users from interacting with the social media links.
*   **Severity:** Critical (UI/UX Functionality Blocker)
*   **Steps to Reproduce:**
    1. Open the Team / Instructors Module page.
    2. Locate any mentor profile card grid node.
    3. Hover the mouse cursor directly over the mentor's background photo.
*   **Actual Result:** Darkened opacity overlay fails to trigger, leaving social links hidden and unclickable.
*   **Expected Result:** Hover state instantly triggers opacity overlay and renders accessible social media links.

---

## 5. Conclusion & Recommendations

While the overall platform architecture shows robust structural stability across most tested flows, the final Quality Gate status is currently **❌ REJECTED (Fixes Required)** pending the immediate resolution of the two critical release blockers identified in the Courses Catalog (ID: T297) and Team / Instructors (ID: T337) modules.

*   **Quality Gate Status:** ❌ REJECTED (Fixes Required)

### 🚨 Critical Release Blockers (Hotfix Required)

1.  **(ID: T297):** Core functional restriction in dynamic course query parsing which completely breaks the search workflow.
2.  **(ID: T337):** UI/UX functionality blocker that prevents overlay interaction and entirely obstructs user access to social media nodes.

### 📋 Next Steps & Action Plan

1.  **Immediate Hotfix Deployment:** A targeted hotfix deployment is strictly requested for both the Courses Catalog (T297) and Team / Instructors (T337) modules. Both defects introduce blocking behaviors that fail baseline deployment quality standards for the production environment and must be resolved before branch closure.
2.  **Sprint Backlog Deferral:** The UI styling regression on the Theory Website Module (T278) causes a visual layout shift but does not impact business logic boundaries. This issue can be safely deferred to the active sprint backlog for post-release processing or concurrent maintenance.
3.  **Regression Cycle Scheduling:** Once development delivers verified source patches for T297 and T337, a targeted manual retest and regression suite must be executed against the catalog search matrix and team card wrappers to validate full Quality Gate compliance.
