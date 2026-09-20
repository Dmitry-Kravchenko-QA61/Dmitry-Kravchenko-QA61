# 📊 Test Summary Report: Web Application Functional & UI Validation

## 1. Project Overview

* **Project Name:** QA Portfolio Validation Suite
* **Environment:** Web Application (QA-Staging environment)
* **Testing Period:** September 2026
* **QA Engineer:** Dmitry Kravchenko

## 2. Objective & Scope

The primary objective of this testing cycle was to verify layout stability, end-to-end navigation flows, and UI/UX layout positioning across desktop screen resolutions. Additionally, the scope included validating functional boundary conditions for input forms, search queries, and data fields, as well as verifying complex interactive sandbox states and dynamic workflows of the web platform's core pages.

**In Scope:**

* 📑 **Theory Website Module:** Core headings, mission blocks, localization, and "accordion" behavior.
* 🔍 **Courses Catalog:** Grid layouts, search accuracy, dynamic sidebar filtering, and sorting behaviors.
* 🐛 **Bugs & Test Cases:** Mock Jira forms, drag-and-drop kanban columns, and state triggers.
* 👥 **Team & Instructors:** Expert profiles, filter tabs, modal biographies, and cross-browser desktop grid layout verification.
* 🏷️ **Brand Identity Media Page:** Media Kit parameters, brand logo assets validation, technical spacing, color hex tokens, and vector file size constraints.


## 3. Test Design & Metrics Summary

A total of 85 manual test cases were executed. The test suite utilized core black-box techniques including equivalence partitioning (EP), boundary value analysis (BVA), and state transition testing to validate UI controls and functional boundaries.


### 📈 Execution Dashboard

| Total Executed | Passed | Failed | Blocked | Pass Rate |
| :---: | :---: | :---: | :---: | :---: |
| 85 | 82 | 3 | 0 | **96.47%** ⚠️ |

### ⚙️ Module Distribution & Findings

| Module / Page | Test Case IDs | Total Tests | Passed | Failed | Status / Defects Found |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Theory Website Module** | T274 – T288 | 15 | 14 | 1 | 🔴 **T278 Failed:** Corporate Values block causes visual layout shift. |
| **Courses Catalog** | T289 – T305 | 17 | 16 | 1 | 🔴 **T297 Failed (Critical):** Catalog search query parsing failure. |
| **Bugs & Test Cases** | T306 – T322 | 17 | 17 | 0 | 🟢 **Stable.** All mock Jira form controls working as intended. |
| **Team / Instructors** | T323 – T341 | 19 | 18 | 1 | 🔴 **T337 Failed:** Hover state transparency overlay blocks social links. |
| **Brand Identity Media Page** | T342 – T358 | 17 | 17 | 0 | 🟢 **Stable.** Asset wrappers and hex copy-to-clipboard passed. |

## 4. Detailed Defect Logs (Discovered Bugs)

### 🐛 Bug #1: Visual Layout Shift on Theory Website Module (ID: T278)
* **Description:** The Corporate Values block causes a minor visual layout shift during standard DOM rendering, leading to a partial text overlap with adjacent components.
* **Severity:** Minor (UI Layout Discrepancy)

### 🐛 Bug #2: Catalog Search Query Parsing Failure (ID: T297)
* **Description:** Typing specific search queries like 'API' into the course search bar does not dynamically update the catalog view grid. The 'API & DB Testing' course card remains hidden, completely blocking users from finding matching content.
* **Severity:** Critical (Core Functional Restriction in Content Discovery)

### 🐛 Bug #3: Hover State Overlay Bug on Team / Instructors Module (ID: T337)
* **Description:** Hovering a cursor over a mentor profile card background photo does not render the darkened opacity overlay correctly. As a result, the social sharing sub-elements remain partially hidden and unclickable, preventing users from interacting with the social links.
* **Severity:** Minor (UI/UX Functionality Bug)
## 5. Conclusion & Recommendations

While the overall platform architecture shows robust structural stability, the Quality Gate status is currently ❌ REJECTED (Fixes Required) pending the resolution of the Critical search filtering restriction found in the Courses Catalog (ID: T297).

* **Quality Gate Status:** ❌ **REJECTED** (Fixes Required)
* **Next Steps:** A hotfix deployment is requested for the **Courses Catalog** module (T297) to restore search functionality prior to release. The UI styling and functionality regressions on the **Theory Website** module (T278) and **Team / Instructors** module (T337) must be moved to the active sprint backlog for immediate post-release or concurrent fixing, as T337 partially blocks user interaction with social links.
