# My Sauce Demo Bug Log

I logged into Sauce Demo using the `problem_user` account and spent time clicking around to find out what was broken. I kept Chrome DevTools open to see what errors were happening behind the scenes. Here are three of the many bugs I discovered:

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
* **Expected result:** It should take you to a page showing that specific item's details and price.
* **Actual result:** It opens a page that says "ITEM NOT FOUND" and the price displays a broken math formula ($\sqrt{-1}$) instead of a regular number.

---

## 🛑 [Checkout] Form doesn't let you finish ordering
* **Severity:** Critical / Blocker
* **Steps to reproduce:**
  1. Add an item to your cart and go to the cart page.
  2. Click the Checkout button.
  3. Type your first name, last name, and zip code into the boxes.
  4. Click the Continue button.
* **Expected result:** The page should save your info and move you to the next step to review your order.
* **Actual result:** The page just refreshes, wipes out everything you typed, and gives a red error saying "Last Name is required" even though you typed it. The text boxes also look squished and broken.
* **DevTools Console:** A red error pops up in the console from the checkout page file right when you click continue.




