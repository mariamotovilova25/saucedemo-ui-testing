# Test Plan: SauceDemo Web Application UI & Functional Testing

## 1. Introduction & Objectives
The objective of this Test Plan is to define the strategy, scope, resources, and schedule for manual functional and UI/UX testing of the **SauceDemo (Swag Labs)** e-commerce platform.

The primary goal is to verify that core end-to-end user journeys (authentication, catalog browsing, cart management, and checkout execution) meet functional requirements and maintain visual integrity across supported devices.

## 2. Test Scope

### 2.1 In-Scope (Features to be tested)
* **Authentication Module:** Login with valid, invalid, locked-out, and problem user accounts; session termination (logout).
* **Inventory Catalog:** Product listing, price accuracy, sorting algorithms (A-Z, Z-A, Low-High, High-Low), image rendering, item details pages.
* **Shopping Cart System:** Dynamic item addition/removal, state persistence across page refreshes, item badge counter updates.
* **Checkout Flow (E2E):** Step 1 form input validation (First Name, Last Name, Zip Code), Step 2 order summary calculations (Item total, Tax, Total), Step 3 order completion state.
* **UI/UX & Responsiveness:** Layout structural alignment, element visibility, text truncation, button clickability across Desktop, Tablet, and Mobile viewports.
* **Error Handling & DevTools Inspection:** Console JS error detection, HTTP status codes validation via Network tab.

### 2.2 Out-of-Scope (Not covered in this test cycle)
* Automated E2E testing using Selenium/Cypress/Playwright (focus is purely manual & diagnostic).
* Backend database integration & server infrastructure load testing.
* Payment gateway processor integrations (mocked data only).

## 3. Test Strategy & Types of Testing

| Testing Type | Description & Focus |
| :--- | :--- |
| **Smoke Testing** | Critical path verification (Login ➔ Add to Cart ➔ Checkout) before detailed test execution. |
| **Functional Testing** | Business logic verification (sorting algorithms, calculations, error message triggers). |
| **UI/UX Testing** | Cross-browser visual consistency, font sizes, colors, component positioning, alignment. |
| **Responsive Testing** | DevTools viewport emulation (Mobile portrait/landscape, Tablet breakpoints). |
| **Boundary & Negative Testing** | Invalid inputs in login/checkout forms, SQL injection-like strings in fields. |
| **Exploratory Testing** | Unstructured testing sessions focused on user behavior anomalies (`problem_user`). |

## 4. Environment & Tools

* **AUT (Application Under Test):** [https://www.saucedemo.com/](https://www.saucedemo.com/)
* **Browsers:** Google Chrome (v126+), Mozilla Firefox (v127+), Apple Safari (v17+)
* **Mobile Viewports (Chrome DevTools):**
  * iPhone 14 Pro (393 × 852 px)
  * Google Pixel 7 (412 × 915 px)
  * iPad Air (820 × 1180 px)
* **Diagnostics:** Chrome DevTools (Console, Network, Elements).
* **Test Documentation:** Markdown / GitHub Repository.

## 5. Entry & Exit Criteria

### 5.1 Entry Criteria
* Test environment (SauceDemo URL) is reachable and operational.
* Requirements and test scenarios are documented and reviewed.
* Chrome DevTools environment is configured for network and viewport emulation.

### 5.2 Exit Criteria
* 100% of planned Critical and High priority Test Cases executed.
* All identified Critical/Blocker defects logged with reproducible steps and DevTools logs.
* Final Test Summary and Bug Reports documented in the repository.

## 6. Risks & Mitigation Strategies

| Identified Risk | Impact | Mitigation Strategy |
| :--- | :--- | :--- |
| Dynamic third-party images failing to load (`problem_user`) | Medium | Inspect Network tab to confirm 404 image request failures vs UI component bugs. |
| Viewport rendering variations across devices | Low | Use standard DevTools resolution breakpoints and cross-browser spot checks. |
