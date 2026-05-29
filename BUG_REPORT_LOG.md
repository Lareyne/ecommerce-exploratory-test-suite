# My Sauce Demo Bug Log

This log documents functional and user interface defects identified on the Sauce Demo platform using the the `problem_user` credentials. Chrome DevTools was kept open during testing to capture underlying system errors.

---

## 🛑 [UI] All product images are broken
* **Severity:** Medium
* **Steps to reproduce:**
1. Go to saucedemo.com
2. Log in as `problem_user`
3. Look at the items on the main store page
* **Expected result:** Each item should show a picture of product that is listed (backpack, shirt, etc.).
* **Actual result:** Every single product shows the exact same picture of a dog.
* **DevTools Console:** The console shows several red network errors saying it failed to load the image links.

---

## 🛑 [Routing] Clicking on a product opens a broken page with a strange price
* **Severity:** High
* **Steps to reproduce:**
1. Go to saucedemo.com
2. Log in using `problem_user` credentials.
3. Click on product name "Sauce Labs Fleece Jacket".
* **Expected result:** The user is routed to a page showing that specific item's details and price.
* **Actual result:** The application opens a page that says "ITEM NOT FOUND" and the price displays a broken math formula ($\sqrt{-1}$) instead of a regular number.
* **DevTools Console:** The console records an immediate breakdown in the page's item routing logic when loading the fallback screen.

---

## 🛑 [Checkout] Form doesn't allow user to complete order
* **Severity:** Critical / Blocker
* **Steps to reproduce:**
1. Go to saucedemo.com
2. Log in using `problem_user` credentials.
3. Add an item to the cart and click the shopping cart icon.
4. Click the Checkout button.
5. Type a first name, last name, and zip code into the fields.
6. Click the Continue button.
* **Expected result:** The page saves the form data and moves the user to the next step to review the order.
* **Actual result:** The checkout form input fields fail to process data correctly. While filling out the Last Name field, the First Name field is instantly wiped out, and text fields only accept singular characters as they are typed. Clicking the Continue button refreshes the page, clears all information, and displays a false warning stating "Error: Last Name is required."
* **DevTools Console:** A red error pops up in the console from the checkout page file right when the continue button is clicked.
