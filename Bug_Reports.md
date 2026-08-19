# Bug Reports: SauceDemo Application Defects

This document contains real defect reports identified during functional, exploratory, and edge-case testing of the SauceDemo platform (specifically targeting user profile anomalies like `problem_user`).


## BUG-001: Incorrect Product Images Rendered Across Catalog (`problem_user`)

* **Defect ID:** BUG-001
* **Summary:** All product cards display a broken generic dog image (`sl-404.jpg`) instead of respective product images for `problem_user`.
* **Severity:** Medium (Major UI/UX Degraded)
* **Priority:** High
* **Component:** Inventory / Product Catalog Page (`/inventory.html`)
* **Environment:** macOS Sonoma 14.5 | Google Chrome (v126.0) | Resolution: 1920x1080

### Steps to Reproduce:
1. Navigate to `https://www.saucedemo.com/`.
2. Log in using Username: `problem_user` and Password: `secret_sauce`.
3. Inspect the product images rendered on `/inventory.html`.

### Expected Result:
Each product card displays its unique image (e.g., Backpack image for "Sauce Labs Backpack", Bike Light image for "Sauce Labs Bike Light").

### Actual Result:
Every product card renders the exact same fallback image (`sl-404.jpg`).

### DevTools Diagnostic Info:
* **Elements Inspector:** Image tag src attribute points to `/static/media/sl-404.a6882801.jpg` for all `<img>` elements within `.inventory_item_img`.
* **Network Tab:** Request `GET /static/media/sl-404.a6882801.jpg` returns `HTTP 200 OK`, confirming static source code binding error rather than asset missing 404.


## BUG-002: "Add to Cart" Event Listener Fails for Specific Products (`problem_user`)

* **Defect ID:** BUG-002
* **Summary:** Clicking "Add to cart" on specific items (e.g., "Sauce Labs Fleece Jacket") fails to trigger cart state update.
* **Severity:** High (Functional Core Flow Blocked)
* **Priority:** High
* **Component:** Inventory / Cart Actions (`/inventory.html`)
* **Environment:** macOS Sonoma 14.5 | Google Chrome (v126.0)

### Steps to Reproduce:
1. Log in as `problem_user`.
2. Locate the "Sauce Labs Fleece Jacket" product card.
3. Click the **Add to cart** button.
4. Observe the Shopping Cart badge and button UI state.

### Expected Result:
Item is added to cart, button text updates to "Remove", and shopping cart badge increments by 1.

### Actual Result:
Button click yields no action. Button text remains "Add to cart", and the cart counter badge does not update.

### DevTools Diagnostic Info:
* **Console Tab:** Uncaught TypeError logged upon click: `Cannot read properties of undefined (reading 'add')`.
* **Network Tab:** No payload dispatch recorded upon button click event.


## BUG-003: Last Name Field Input Truncation / Overwrite on Checkout (`problem_user`)

* **Defect ID:** BUG-003
* **Summary:** Typing into the "Last Name" field on Checkout Step One forces input characters to overwrite existing string or fail form validation.
* **Severity:** Critical (Checkout E2E Flow Blocked)
* **Priority:** Critical
* **Component:** Checkout Module (`/checkout-step-one.html`)
* **Environment:** Windows 11 | Mozilla Firefox (v127.0)

### Steps to Reproduce:
1. Log in as `problem_user`.
2. Add any valid item to cart and proceed to `/checkout-step-one.html`.
3. Type `Maria` into First Name field.
4. Type `Motovilova` into Last Name field.
5. Enter `1000` into Zip/Postal Code field and click **Continue**.

### Expected Result:
Form accepts inputs and transitions user to Checkout Step Two (`/checkout-step-two.html`).

### Actual Result:
Form submission is rejected with error: `"Error: Last Name is required"`. Input handler fails to bind string state to Last Name input payload.
