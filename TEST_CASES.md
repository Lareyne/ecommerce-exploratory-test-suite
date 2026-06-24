# Sauce Demo Functional Test Cases

This document contains the functional test cases I wrote to test the core inventory, product pages, and checkout flow on the Sauce Demo website. 

---

## 📊 Requirement Traceability Matrix (RTM)

This matrix maps the basic requirements of the site to the test cases I created, showing which tests failed and where to find the bug reports in my `BUG_REPORT_LOG.md`.

| Requirement ID | Requirement Description | Test Case ID | Test Case Summary | Status | Linked Bug |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **REQ-INV-01** | Product images must match the listed item name and description. | `TC-INV-001` | Verify that product images load correctly on the main page. | ❌ **FAILED** | Bug #1: All product images are broken |
| **REQ-RT-02** | Clicking a product name must open the correct details page and price. | `TC-RT-002` | Verify that clicking a product opens its specific details page. | ❌ **FAILED** | Bug #2: Product opens a broken page |
| **REQ-CHK-03**| The checkout form must accept user details and go to the final review page. | `TC-CHK-003` | Verify that the checkout form can be filled out and submitted. | ❌ **FAILED** | Bug #3: Form doesn't allow user to complete order |

---

## 📝 Detailed Test Cases

### 🛠️ Main Store Page (Inventory)

#### **Test Case ID:** `TC-INV-001`
* **Description:** Check that all item images on the main page show the correct product picture instead of placeholders or broken links.
* **Pre-conditions:** The user is on the main login screen.
* **Test Data:** URL: `https://www.saucedemo.com/`, Username: `problem_user`

| Step # | Test Steps | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Go to saucedemo.com. | The login page loads up fine. | As expected. | PASS |
| 2 | Enter the credentials and click the "Login" button. | The user logs in and lands on the main store page (`/inventory.html`). | As expected. | PASS |
| 3 | Look closely at the product images for all items. | Every item should have its own matching picture (like a backpack or jacket). | Every single item shows a picture of a dog. DevTools shows network errors. | **FAIL** |

---

### 🔄 Clicking Products (Routing)

#### **Test Case ID:** `TC-RT-002`
* **Description:** Check that clicking on an individual product name link successfully opens the details page for that specific item with the right price.
* **Pre-conditions:** The user is logged in and looking at the main store page.
* **Test Data:** Clicked Item: "Sauce Labs Fleece Jacket"

| Step # | Test Steps | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Find the "Sauce Labs Fleece Jacket" link on the page. | The link is visible and can be clicked. | As expected. | PASS |
| 2 | Click on the product name link. | The page for the jacket opens up showing the correct details and a price of $49.99. | The page says "ITEM NOT FOUND" and the price displays as "-1". | **FAIL** |

---

### 🛒 Checkout Flow

#### **Test Case ID:** `TC-CHK-003`
* **Description:** Check that the checkout information form allows the user to type in their details and click through to the next page.
* **Pre-conditions:** The user has added an item to the cart and clicked the "Checkout" button (`/checkout-step-one.html`).
* **Test Data:** First Name: `John`, Last Name: `Doe`, Zip Code: `12345`

| Step # | Test Steps | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Click into the "First Name" box and type "John". | The box displays the text "John". | As expected. | PASS |
| 2 | Click into the "Last Name" box and type "Doe". | The box displays "Doe". The First Name field should still say "John". | Typing the last name instantly deletes the first name. The boxes only let me type one letter at a time. | **FAIL** |
| 3 | Try to fill out the rest and click the "Continue" button. | The form saves the text and goes to the order review page (`/checkout-step-two.html`). | The form clears out completely and shows an error saying the Last Name is required. | **FAIL** |
