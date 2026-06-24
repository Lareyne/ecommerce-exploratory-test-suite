# Sauce Demo Test Cases

This document lists the step-by-step tests I performed on the Sauce Demo website using the `problem_user` login. 

---

## 🛠️ 1. Main Store Page Tests

**Test Goal:** Make sure all the product images on the main page match the items being sold.

* **How to test:**
  1. Go to `https://www.saucedemo.com/`
  2. Log in using the username `problem_user`
  3. Look at the pictures for the items on the main store screen.
* **What should happen (Expected):** Every item should show its own correct product picture (like a backpack or a shirt).
* **What actually happened (Actual):** ❌ **FAILED.** Every single product shows the exact same picture of a dog. (See Bug #1 in my Bug Log).

---

## 🔄 2. Clicking Product Links Tests

**Test Goal:** Make sure clicking a product's name takes you to the correct details page with the right price.

* **How to test:**
  1. Log in to the site.
  2. Click on the text link for the "Sauce Labs Fleece Jacket".
* **What should happen (Expected):** The page for the jacket should open up showing its description and the correct price ($49.99).
* **What actually happened (Actual):** ❌ **FAILED.** The page opens up but says "ITEM NOT FOUND" and the price shows up as a broken "-1". (See Bug #2 in my Bug Log).

---

## 🛒 3. Checkout Form Tests

**Test Goal:** Make sure a user can fill out the checkout form and submit it successfully.

* **How to test:**
  1. Add any item to the shopping cart and click the checkout button.
  2. Type "John" into the First Name box.
  3. Type "Doe" into the Last Name box.
  4. Type "12345" into the Zip Code box.
  5. Click the "Continue" button.
* **What should happen (Expected):** The form should save your name and take you to the final order review page.
* **What actually happened (Actual):** ❌ **FAILED.** Typing the last name instantly deletes the first name from the box. When you click continue, the form resets and says the last name is missing. (See Bug #3 in my Bug Log).
