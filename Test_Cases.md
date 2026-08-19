# Test Cases: SauceDemo E-Commerce Application

This document outlines structured manual test cases covering key business flows, UI validation, edge cases, and boundary conditions for the SauceDemo application.


## Module 1: Authentication & Authorization

### TC-AUTH-001: Successful Login with Valid Credentials
* **Priority:** High | **Severity:** Major
* **Preconditions:** User is on the login page (`https://www.saucedemo.com/`).
* **Test Steps:**
  1. Enter `standard_user` into the **Username** input field.
  2. Enter `secret_sauce` into the **Password** input field.
  3. Click the **Login** button.
* **Expected Result:** User is successfully redirected to the inventory page (`/inventory.html`). Inventory header displays "Products". Cart icon is visible.



### TC-AUTH-002: Login Attempt with Locked-Out User Account
* **Priority:** High | **Severity:** Major
* **Preconditions:** User is on the login page.
* **Test Steps:**
  1. Enter `locked_out_user` into the **Username** input field.
  2. Enter `secret_sauce` into the **Password** input field.
  3. Click the **Login** button.
* **Expected Result:** User remains on the login page. An error banner is displayed: `"Epic sadface: Sorry, this user has been locked out."`. Red error icons appear on input fields.



### TC-AUTH-003: Login Validation for Empty Credentials
* **Priority:** Medium | **Severity:** Minor
* **Preconditions:** User is on the login page.
* **Test Steps:**
  1. Leave **Username** and **Password** fields empty.
  2. Click the **Login** button.
* **Expected Result:** Form submission is blocked. An error banner is displayed: `"Epic sadface: Username is required"`.



## Module 2: Inventory Catalog & Sorting

### TC-INV-001: Product List Sorting (Price Low to High)
* **Priority:** Medium | **Severity:** Moderate
* **Preconditions:** User is logged in as `standard_user` and located on `/inventory.html`.
* **Test Steps:**
  1. Click on the product sort dropdown (top right, default "Name (A to Z)").
  2. Select the option `"Price (low to high)"`.
* **Expected Result:** Product list immediately re-orders. The first item displayed is "Sauce Labs Onesie" ($7.99), and the last item is "Sauce Labs Fleece Jacket" ($49.99). Prices follow strict ascending numerical order.



### TC-INV-002: Cart Counter Badge Incrementation & Decrementation
* **Priority:** High | **Severity:** Major
* **Preconditions:** User is logged in. Shopping cart is empty (no numeric badge).
* **Test Steps:**
  1. Click **Add to cart** on "Sauce Labs Backpack".
  2. Observe cart icon badge and button state.
  3. Click **Add to cart** on "Sauce Labs Bike Light".
  4. Click **Remove** on "Sauce Labs Backpack".
* **Expected Result:**
  * Step 2: Badge shows `1`. Button changes to "Remove".
  * Step 3: Badge updates to `2`.
  * Step 4: Badge decreases to `1`.



## Module 3: Shopping Cart & Checkout Flow (End-to-End)

### TC-CHK-001: End-to-End Order Execution (Happy Path)
* **Priority:** Critical | **Severity:** Blocker
* **Preconditions:** User is logged in with 1 item ("Sauce Labs Backpack" - $29.99) added to the cart.
* **Test Steps:**
  1. Click the shopping cart container icon.
  2. On `/cart.html`, verify item name and price ($29.99), then click **Checkout**.
  3. On `/checkout-step-one.html`, enter:
     * First Name: `Maria`
     * Last Name: `Motovilova`
     * Zip/Postal Code: `1000`
  4. Click **Continue**.
  5. On `/checkout-step-two.html`, verify Item Total ($29.99), Tax ($2.40), and Total ($32.39).
  6. Click **Finish**.
* **Expected Result:** Redirected to `/checkout-complete.html`. Header displays `"Thank you for your order!"`. Cart badge is cleared.



### TC-CHK-002: Checkout Form Validation (Missing Mandatory Fields)
* **Priority:** High | **Severity:** Major
* **Preconditions:** User is on `/checkout-step-one.html` with items in the cart.
* **Test Steps:**
  1. Enter `Maria` into First Name field.
  2. Leave Last Name and Postal Code fields blank.
  3. Click **Continue**.
* **Expected Result:** Transition to Step Two is prevented. Error message displays: `"Error: Last Name is required"`.



## Module 4: Anomaly & Edge Case Testing (`problem_user`)

### TC-EDGE-001: Visual & Functional Verification under Problem User Profile
* **Priority:** Medium | **Severity:** Moderate
* **Preconditions:** Logged in using username `problem_user`.
* **Test Steps:**
  1. Navigate to `/inventory.html`.
  2. Inspect product images across items.
  3. Attempt to add "Sauce Labs Fleece Jacket" to the cart.
* **Expected Result (Documenting Defects):** 
  * All product images display the same fallback image (`sl-404.jpg`).
  * "Add to cart" button fails for certain items due to broken event listeners. (Logged in Bug Reports).
