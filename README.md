# E-Commerce Web Application UI & Functional Testing (SauceDemo)
![QA Standard](https://img.shields.io/badge/QA-Manual%20%26%20UI%20Testing-blue)
![Tools](https://img.shields.io/badge/Tools-Chrome%20DevTools%20%7C%20Jira%20%7C%20GitHub-orange)
![Coverage](https://img.shields.io/badge/Testing-Functional%20%7C%20UI%2FUX%20%7C%20Responsive-green)

Comprehensive End-to-End manual and functional testing project for the [SauceDemo](https://www.saucedemo.com/) e-commerce platform. The goal of this project is to validate core user journeys, UI/UX consistency, responsive layout integrity, and edge-case error handling using standard software testing practices.


## Project Overview & Scope
* **Target Application:** SauceDemo (Swag Labs) E-Commerce Web App
* **Testing Types Executed:** Functional Testing, UI/UX & Responsive Testing, Boundary & Negative Testing, Smoke & Regression Testing, Exploratory Session Testing.
* **Testing Environments & Browsers:**
  * **Desktop:** Chrome (v126+), Firefox (v127+), Safari (v17+)
  * **Mobile Viewports (DevTools):** iPhone 14 Pro (393x852), Pixel 7 (412x915), iPad Air (820x1180)

## Repository Structure & Artifacts
| Document / Artifact | Description |
| :--- | :--- |
|  [`Test_Plan.md`](./Test_Plan.md) | Quality strategy, test scope, environment breakdown, and risk analysis. |
|  [`Test_Cases.md`](./Test_Cases.md) | Structured test cases covering Authentication, Catalog, Cart, and Checkout flows. |
|  [`Bug_Reports.md`](./Bug_Reports.md) | Detailed defect reports including execution steps, DevTools console logs, and severity classification. |
|  [`Responsive_Matrix.md`](./Responsive_Matrix.md) | UI layout validation across desktop, tablet, and mobile breakpoints. |


## Key Features & User Flows Tested
1. **Authentication & Authorization:**
   * Valid user login (`standard_user`).
   * Locked-out user handling (`locked_out_user`).
   * Performance and visual anomaly testing (`problem_user`, `performance_glitch_user`).
   * Invalid credentials and empty input validation.

2. **Inventory & Product Management:**
   * Sorting algorithms (A-Z, Z-A, Price Low-High, Price High-Low).
   * Item details navigation and consistency between grid and detail views.
   * Dynamic cart counter updates upon adding/removing items.

3. **Cart & Checkout Lifecycle (End-to-End):**
   * Persisted state validation across browser navigation.
   * Multi-item aggregation and tax/total calculations.
   * Checkout form validation (First Name, Last Name, Zip Code).
   * Complete order confirmation flow.


## Tools & Technologies Used
* **Documentation & Management:** Markdown, Jira / GitHub Issues format.
* **Web Diagnostics:** Chrome DevTools (Console, Network payload inspection, Mobile Device Emulation, Element Inspector).
* **Browsers:** Google Chrome, Mozilla Firefox, Apple Safari.

## Author
**Maria Motovilova** — Junior QA Engineer  
* LinkedIn: [linkedin.com/in/maria-motovilova-a4a22335a](https://www.linkedin.com/in/maria-motovilova-a4a22335a/)  
* GitHub: [github.com/mariamotovilova25](https://github.com/mariamotovilova25)
