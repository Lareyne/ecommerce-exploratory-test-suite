# 📊 Technical Bug Report Log - Sauce Demo

This log documents critical UI/UX and functional system defects identified during an exploratory testing session on the Sauce Demo platform using `problem_user` credentials. 

---

## 🛑 Bug 1: Global Broken Asset Links (UI Defect)
* **Severity:** Medium
* **Environment:** Production (Google Chrome Browser)
* **Steps to Reproduce:**
  1. Navigate to `https://saucedemo.com`
  2. Log in using `problem_user` credentials.
  3. Observe the product catalog grid layout.
* **Expected Result:** Each product container renders its unique, high-resolution product image asset.
* **Actual Result:** The system fails to fetch individual asset links. Every single product uniformly falls back to the exact same dog placeholder image.
* **System/Console Impact:** DevTools Console captures multiple red network resource errors (`ERR_FAILED`) while trying to load the unique image paths.

---

## 🛑 Bug 2: Broken Product Redirection & Pricing String (Functional Defect)
* **Severity:** High
* **Environment:** Production (Google Chrome Browser)
* **Steps to Reproduce:**
  1. Navigate to the main store page as a logged-in `problem_user`.
  2. Click directly on any specific product title link (e.g., "Sauce Labs Backpack").
* **Expected Result:** The application safely routes the user to a dedicated product details panel displaying valid pricing and descriptions.
* **Actual Result:** Core routing fails. The system throws a generic "ITEM NOT FOUND" text fallback screen. Furthermore, the currency text string breaks completely, displaying a mathematical formula (`$\sqrt{-1}`) instead of a real item price.

---

## 🛑 Bug 3: Checkout Form Input Validation & Layout Collapse (Blocker)
* **Severity:** Critical
* **Environment:** Production (Google Chrome Browser)
* **Steps to Reproduce:**
  1. From the cart menu, click "Checkout" to advance to `checkout-step-one.html`.
  2. Populate the "First Name", "Last Name", and "Zip/Postal Code" text boxes with valid strings.
  3. Click the green "Continue" button.
* **Expected Result:** Form successfully reads values, passes data validations, and advances to the final order overview pane.
* **Actual Result:** The DOM layout collapses (the text box inputs are visually squished). Upon submission, the form clears all fields, blocks pipeline progression, and throws a false warning stating that the required last name is missing.
* **System/Console Impact:** Fires an unhandled asynchronous execution error directly from the checkout source page.
