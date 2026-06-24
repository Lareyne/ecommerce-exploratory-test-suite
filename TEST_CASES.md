# Sauce Demo Test Cases

This document lists the step-by-step tests I performed on the Sauce Demo website using the `problem_user` login. Each test case maps directly to a bug and an evidence screenshot in this repository.

---

## 🛠️ 1. Main Store Page Tests

**Test Goal:** Make sure all the product images on the main page match the items being sold.

* **How to test:**
  1. Go to `https://www.saucedemo.com/`
  2. Log in using the username `problem_user`
  3. Look at the pictures for the items on the main store screen.
* **What should happen (Expected):** Every item should show its own correct product picture (like a backpack or a shirt).
* **What actually happened (Actual):** ❌ **FAILED.** Every single product shows the exact same picture of a dog. The DevTools console shows multiple red `net::ERR_FAILED` network errors.
* **Linked Evidence:** 
  * See **Bug #1** in `BUG_REPORT_LOG.md`
  * View screenshot evidence: `Bug 1.png`

---

## 🔄 2. Clicking Product Links Tests

**Test Goal:** Make sure clicking a product's name takes you to the correct details page with the right price.

* **How to test:**
  1. Log in to the site.
  2. Click on the text link for the "Sauce Labs Fleece Jacket".
* **What should happen (Expected):** The page for the jacket should open up showing its description and the correct price ($49.99).
* **What actually happened (Actual):** ❌ **FAILED.** The page opens up but displays a generic "ITEM NOT FOUND" text message next to the dog picture. The price shows up as a broken math formula (`$\sqrt{-1}$`).
* **Linked Evidence:** 
  * See **Bug #2** in `BUG_REPORT_LOG.md`
  * View screenshot evidence: `Bug 2.png`

---

## 🛒 3. Checkout Form Tests

**Test Goal:** Make sure a user can fill out the checkout form and submit it successfully.

* **How to test:**
  1. Add any item to the shopping cart and click the checkout button.
  2. Type your information into the First Name, Last Name, and Zip Code boxes.
  3. Click the "Continue" button.
* **What should happen (Expected):** The form should accept your text, keep all fields filled, and take you to the final order review page.
* **What actually happened (Actual):** ❌ **FAILED.** Typing a letter into the Last Name field instantly wipes out the First Name field (leaving only a single character behind). Clicking continue displays a false error message saying "Error: Last Name is required."
* **Linked Evidence:** 
  * See **Bug #3** in `BUG_REPORT_LOG.md`
  * View screenshot evidence: `Bug 3.png`
